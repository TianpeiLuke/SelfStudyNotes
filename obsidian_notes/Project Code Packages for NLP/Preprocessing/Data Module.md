---
tags:
  - project
  - code
  - code_snippet
  - mlops/preprocessing
  - buyer_seller_messaging
  - natural_language_processing
keywords:
  - pytorch/lightning
topics: 
language: python
date of note: 2024-04-05
---

## Code Snippet Summary

>[!important]
>`BSMDataset` inherits `orch.utils.data.Dataset` and allow us to inject `Pipeline` when accessing data item.
>- `BSMDataset` process the data when accessing it instead of processing all of them beforehand. 
>- `BSMDataset` is used to create PyTorch `DataLoader`. 

- 

## Code

```python
class BSMDataset(Dataset):
    def __init__(self, config: Dict[str, Union[str, List[str], int]], 
                       file_dir: Optional[str] = None, 
                       filename: Optional[str] = None,
                       dataframe: Optional[pd.DataFrame] = None
                ) -> None:
        self.config = config 
        
        self.header = ...
        self.label_name = ...
        self.text_name = ...
        
        self.full_field_list = ...
        self.cat_field_list = ...
        self.tab_field_list = ...
            
        self.need_language_detect = ...
        self.processor_pipelines  = dict()
        self.DataReader = None    
        
        # call load_data or load_dataframe according the suffix of the filename
        if file_dir and filename:
            self.file_dir = file_dir
            self.filename = filename
            self.processed_filename = os.path.splitext(filename)[0] + "-processed" + os.path.splitext(filename)[1]
        
            if os.path.splitext(filename)[1] == '.tsv':
                print("load tsv file: ",filename)
                self.sep = '\t'
            elif os.path.splitext(filename)[1] == '.csv':
                print("load csv file: ",filename)
                self.sep = ','   
            else:
                self.sep = ','
            self.load_data()
        elif dataframe is not None and isinstance(dataframe, pd.DataFrame):
            self.load_dataframe(dataframe)
        else:
            raise TypeError('Please input the file directory and filename or the pandas.Dataframe')
    
    # Load data or dataframe
    def load_data(self, **kwargs):
	    ...
	
	def load_dataframe(self, dataframe):
		...
	
	# implement length check
	def __len__(self):
		...
		
    # Missing Value Handling
    def fill_missing_value(self, **kwargs):
	    ...
	    
    # `Pipeline` injection
    def initialize_pipeline(self):
	    ...
	    
	def add_pipeline(self, field_name: str, processor_pipeline: Pipeline):
		...
		
	def text_process(self, row: dict, text_name: str) -> Tuple[str, str]:
		...
		
	# Process data via `Pipeline` 
	def text_process(self, row: dict, text_name: str) -> Tuple[str, str]:
		...
	
	def tokenize_process(self, row: Dict[str, Union[str, float, int]], text_name: str) -> Union[Tuple[torch.tensor, torch.tensor], torch.tensor]:
		...
	
    def label_process(self, row: Dict[str, Union[str, float, int]], label_name: str) -> List[Union[float, int]]:
	    ...
	
    # ========= overwrite item access, allowing processing first ======
    def __getitem__(self, idx):
	    ...		
```

#### Load Data

```python
	...
	
    def load_data(self, **kwargs):
        '''
        load data from disk into pandas.DataFrame
        save
        '''
	    # pd.read_csv based on parameters: 
	    #   self.filename, 
	    #   self.file_dir, 
	    #   self.full_field_list
	    # save to self.DataReader
	    # read_csv depending on whether or not header and full column names are provided
        if 'filename' in kwargs:
            self.filename = kwargs['filename']
        if 'file_dir' in kwargs:
            self.file_dir = kwargs['file_dir']
        if 'full_field_list' in kwargs:
            self.full_field_list = kwargs['full_field_list']
        
        if self.full_field_list is None and 'full_field_list' not in kwargs:
            self.DataReader = pd.read_csv(os.path.join(self.file_dir, self.filename), sep=self.sep, index_col=None)
        else:
            self.DataReader = pd.read_csv(os.path.join(self.file_dir, self.filename), header=0, names=self.full_field_list,  sep=self.sep, index_col=None)

    def load_dataframe(self, dataframe):
	    # if the input is a pandas.DataFrame, then save dataframe itself
	    ...
        if dataframe is not None and isinstance(dataframe, pd.DataFrame):
            if self.full_field_list and len(self.full_field_list) == len(dataframe.columns):
                dataframe.columns = self.full_field_list
            self.DataReader = dataframe
            #self.full_field_list = list(self.DataReader.columns)
        else:
            raise TypeError('Input must be a pandas.DataFrame')
            
    def __len__(self):
        return len(self.DataReader)
```


#### Set field names

```python
	...
	#==================================================
	# add methods to set internal field names ...
	# e.g. set_text_field_name(self, text_field_name), ...
	#====================================================
    def set_text_field_name(self, text_name: str):
		...
		
	def set_label_field_name(self, label_name: str):
		...
		
    def set_cat_field_list(self, cat_field_list: List[str]):
	    ...
	    
    def set_full_field_list(self, full_field_list: List[str]):
	    ... 
```


#### Missing Value Handling

```python
	...
    def fill_missing_value(self, **kwargs):
        '''
         Fill missing value in given columns. Default value is -1.
         
         label_name: the name for label columns, fill in default = 0
         cat_field_list: the list of names for categorical columns, fill in default = ''
         
        '''
        # call pd.DataFrame.fillna()
        # fill-in value according to field type
        # numerical -> -1
        # text -> ''
        # label -> 0
        if self.DataReader is None:
            return
        
        for key, value in kwargs.items():
            if key == 'label_name':
                self.label_name = value         
            if key == 'cat_field_list':
                self.column_cat_name = value
        
        for feature in self.DataReader.columns:
            if feature in self.label_name:
                self.DataReader[feature].fillna(0, inplace=True) 
                self.DataReader[feature] = self.DataReader[feature].astype(int)
            elif feature in self.cat_field_list:
                self.DataReader[feature] = self.DataReader[feature].astype(str)
                self.DataReader[feature].fillna('', inplace=True)          
            else:
                self.DataReader[feature] = self.DataReader[feature].astype(float)
                self.DataReader[feature].fillna(-1, inplace=True)   
```

#### `Pipeline` injection

```python
	...
	# ============== Pipeline injection ========================
    def initialize_pipeline(self):
        self.processor_pipelines = dict()
         
    def add_pipeline(self, field_name: str, processor_pipeline: Pipeline):
        '''
        Add TextProcessorPipeline class object. 
        '''
        if isinstance(field_name, str) and isinstance(processor_pipeline, Pipeline):
            self.processor_pipelines[field_name] = processor_pipeline
        else:
            raise TypeError("Please input the field_name as str type and processor_pipeline as Pipeline class. The current input type is {} and {}.".format(type(text_field), type(processor_pipeline)))
```

#### Process data via `Pipeline` 

```python
	...
    # ============== Text Processing by Pipeline ==================    
    def text_process(self, row: dict, text_name: str) -> Tuple[str, str]:
        '''
        Pre-process text, calling the TextProcessorPipeline to process the text
        '''
        if text_name not in row:
            raise ValueError('Please choose text name in given row or default .text_name')
        
        message = str(row[text_name])
        if len(self.processor_pipelines) == 0:
            # if no text processor then do not process text
            return message, None
        elif text_name not in self.processor_pipelines:
            return message, None
        else:
            # call processor_pipeline to process the field
            if not isinstance(self.processor_pipelines[text_name], TextProcessorPipeline):
                raise TypeError(f'The given pipeline type {type(self.processor_pipelines[text_name])} is not TextProcessorPipeline.')
            filtered_message, language = self.processor_pipelines[text_name](message)
            return filtered_message, language
        

    def tokenize_process(self, row: Dict[str, Union[str, float, int]], text_name: str) -> Union[Tuple[torch.tensor, torch.tensor], torch.tensor]:
        '''
         Tokenization process, calling the TokenizationPipeline to process the text
        '''
        if text_name not in row:
            raise ValueError('Please choose text name in given row or default .text_name')
        
        message = str(row[text_name])
        if len(self.processor_pipelines) == 0:
            # if no text processor then do not process text
            token_len = len(message.split())
            return torch.zeros([1, token_len]), torch.zeros([1, token_len])
        elif text_name not in self.processor_pipelines:
            token_len = len(message.split())
            return torch.zeros([1, token_len]), torch.zeros([1, token_len])
        else:
            # call processor_pipeline to process the field
            if not isinstance(self.processor_pipelines[text_name], TokenizationPipeline):
                raise TypeError(f'The given pipeline type {type(self.processor_pipelines[text_name])} is not TokenizationPipeline.')
                
            input_ids, attention_mask = self.processor_pipelines[text_name](message)
            return input_ids, attention_mask 
        
        
    def label_process(self, row: Dict[str, Union[str, float, int]], label_name: str) -> List[Union[float, int]]:
        '''
         Tokenization process, calling the TokenizationPipeline to process the text
        '''
        if label_name not in row:
            raise ValueError('Please choose text name in given row or default .label_name')
        
        label = row[label_name]
        if (len(self.processor_pipelines) == 0) or (label_name not in self.processor_pipelines):
            return label
        else:
            # call processor_pipeline to process the field
            if not isinstance(self.processor_pipelines[label_name], LabelProcessorPipeline):
                raise TypeError(f'The given pipeline type {type(self.processor_pipelines[label_name])} is not LabelProcessorPipeline.')            
        
            processed_label = self.processor_pipelines[label_name](label)
            return processed_label
```

#### Data Access

```python
	...
	
    # ========= overwrite item access, allowing processing first ======
    def __getitem__(self, idx):
        if torch.is_tensor(idx):
            idx = idx.tolist()
            
		# get the chunk from list of ids
        chunk = self.DataReader.iloc[idx, :].to_dict()
        
        # call Text_Processor to process the text field; if not available, not to process it.
        if self.processor_pipelines:
            for field_name in self.processor_pipelines:
                #text_field_name = field_name #self.text_name
                pipeline_name = self.processor_pipelines[field_name].get_name()

                # check if it is preprocessing pipeline or tokenization pipeline
                if pipeline_name == 'text_process_pipeline':
                    # Text Preprocessing Pipeline
                    filtered_message, language = self.text_process(chunk, field_name)
                    if field_name.islower():
                        processed_text_field_name = field_name + '_processed'
                        language_field_name = 'language'
                    else: 
                        processed_text_field_name = field_name + '_PROCESSED'
                        language_field_name = 'LANGUAGE'
                        
                    # language detect
                    if self.need_language_detect:  #language is not None:
                        if language is None: 
                            language = 'en'
                        chunk[language_field_name] = language
        
                    if 'text_field_overwrite' in self.config and self.config['text_field_overwrite'] == True:
                        chunk[field_name] = filtered_message
                    else:
                        # save to a new column
                        chunk[processed_text_field_name] = filtered_message
                elif pipeline_name == 'tokenization_pipeline':
                    # Tokenization Pipeline
                    input_ids, attention_mask = self.tokenize_process(chunk, field_name)
                        
                    # save tokenized input ids and attention mask to a new column
                    chunk[field_name + '_input_ids'] = input_ids[0]
                    chunk[field_name + '_attention_mask'] = attention_mask[0]
                elif pipeline_name == 'label_process_pipeline':
                    # Label Process Pipeline
                    processed_label = self.label_process(chunk, field_name)
                    
                    if 'text_field_overwrite' in self.config and self.config['text_field_overwrite'] == True:
                        chunk[field_name] = processed_label
                    else:
                        # save to a new column
                        processed_label_field_name = field_name + '_transformed'
                        chunk[processed_label_field_name] = processed_label
                    
                else:
                    raise TypeError(f'{field_name} should be a predefined text field name. The predefined text field name {text_field_name}')
        return chunk 
```

-----------
##  Recommended Notes

- [[Processing Pipelines for Contacts Entry Point]]
	- [[Data Module - Huggingface dataset]]
	- [[Data Module - LightningDataModule]]
- [[Hugging Face datasets doc excerpt 1 overview]]
- [[Pytorch Lightning 7 Data Module]]

- [[Design Pattern Strategy Pattern]]