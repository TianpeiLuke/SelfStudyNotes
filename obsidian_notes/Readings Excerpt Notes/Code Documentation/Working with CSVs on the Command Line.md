---
tags:
  - blog_post
  - excerpt
  - code_package
  - linux/grep
  - bash/awk
aliases: 
keywords: 
topics:
  - command_line_script
language: bash
date of note: 2024-04-26
name: Working with CSVs on the Command Line by Brian Connelly
version: 
year: 2018
---

>[!quote]
> Comma-separated values (CSV), and its close relatives (e.g., Tab-separated values) play a very important role in open access science. CSV is an informally-defined file format that stores tabular data (think spreadsheets) in plain text. Within the file, each row contains a record, and each field in that record is separated by a comma, tab, or some other character. This format offers several significant advantages. Because they are plain text, these files can be easily read and edited without the need for specialized or proprietary software. CSVs are also version-independent, so ten years down the road you won’t have to track down some ancient piece of software in order to revisit your data (or do the same for someone else’s data). Support for CSV files is built into most data analysis software, programming languages, and online services (see [Some Useful Resources](http://bconnelly.net/working-with-csvs-on-the-command-line/#some-useful-resources) at the end of this article for links for your software of choice).
> 
> To many, the command line (or _shell_) is a strange and scary place. Those familiar with working in the command line, however, wouldn’t trade its power, speed, and flexibility for anything, no matter how shiny or “user friendly” an alternative drag-and-drop interface might be. This power, speed, and flexibility extends to working with CSV files, and it’s here that I’d like to demonstrate a small slice of what can be done with just a few keystrokes. Even though the Unix command line has existed for decades, it’s still always just a few clicks away, whether you use Linux on some HPC hardware or cloud service, or whether you use Mac OS X on your laptop.
> 
> You don’t have to be a command line wizard to use the commands below, but you do need to know the basics of how to get to a command line (hint for OS X users, it’s through the Terminal app) and how to do things like changing directories (`cd`) and listing files (`ls`). If these topics are new to you, there’s a pretty good introduction linked below in [Some Useful Resources](http://bconnelly.net/working-with-csvs-on-the-command-line/#some-useful-resources). I’ve also included a brief description of the command line tools used in this cookbook below in [A Quick Overview of the Commands Used in this Cookbook](http://bconnelly.net/working-with-csvs-on-the-command-line/#a-quick-overview-of-the-commands-used-in-this-cookbook). In the next section, I’ll quickly introduce two of the command line’s most powerful features: pipes and output redirection. If you’re already familiar with these, you can jump right into the good stuff.
> 
> This guide is intended to be used like a cookbook. Although you can read it from start to finish (it’s not _that_ long), each “recipe” is a self-contained guide for doing a particular task with a CSV file.
> 
> Although we’re focusing on comma-separated values, all of the commands below would work for data separated by tabs or any other separator. Just replace the comma character in the commands with your delimiter of choice. Most software that handles CSVs isn’t picky, and allows you to specify the delimiter used.

>[!important]
> Contents
> 
> - [A Quick Introduction to Pipes and Redirection](http://bconnelly.net/working-with-csvs-on-the-command-line/#a-quick-introduction-to-pipes-and-redirection)
>     - [Writing Output to a File with Output Redirection](http://bconnelly.net/working-with-csvs-on-the-command-line/#writing-output-to-a-file-with-output-redirection)
>     - [Connecting Programs with Pipes](http://bconnelly.net/working-with-csvs-on-the-command-line/#connecting-programs-with-pipes)
> - [Cleaning Up CSV Files](http://bconnelly.net/working-with-csvs-on-the-command-line/#cleaning-up-csv-files)
>     - [Removing Comments](http://bconnelly.net/working-with-csvs-on-the-command-line/#removing-comments)
>     - [Removing Headers](http://bconnelly.net/working-with-csvs-on-the-command-line/#removing-headers)
>     - [Changing Delimiters](http://bconnelly.net/working-with-csvs-on-the-command-line/#changing-delimiters)
> - [Getting Information about the Data Set](http://bconnelly.net/working-with-csvs-on-the-command-line/#getting-information-about-the-data-set)
>     - [Taking a Peek at the Data Set](http://bconnelly.net/working-with-csvs-on-the-command-line/#taking-a-peek-at-the-data-set)
>     - [Determining the Number of Rows](http://bconnelly.net/working-with-csvs-on-the-command-line/#determining-the-number-of-rows)
>     - [Determining the Number of Columns](http://bconnelly.net/working-with-csvs-on-the-command-line/#determining-the-number-of-columns)
> - [Combining CSVs](http://bconnelly.net/working-with-csvs-on-the-command-line/#combining-csvs)
>     - [Combining Rows from Two or More CSVs](http://bconnelly.net/working-with-csvs-on-the-command-line/#combining-rows-from-two-or-more-csvs)
>     - [Combining Columns from Multiple CSVs](http://bconnelly.net/working-with-csvs-on-the-command-line/#combining-columns-from-multiple-csvs)
> - [Extracting Data Subsets](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-data-subsets)
>     - [Extracting Specific Row Numbers from CSVs](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-specific-row-numbers-from-csvs)
>     - [Extracting Rows Based on Some Value](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-rows-based-on-some-value)
>     - [Extracting Columns](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-columns)
> - [Working with Compressed CSV Files](http://bconnelly.net/working-with-csvs-on-the-command-line/#working-with-compressed-csv-files)
>     - [Compressing CSV Files with bzip2](http://bconnelly.net/working-with-csvs-on-the-command-line/#compressing-csv-files-with-bzip2)
>     - [Working with bzip2-Compressed CSV Files](http://bconnelly.net/working-with-csvs-on-the-command-line/#working-with-bzip2-compressed-csv-files)
>     - [Compressing CSV Files with gzip](http://bconnelly.net/working-with-csvs-on-the-command-line/#compressing-csv-files-with-gzip)
>     - [Working with gzip-Compressed CSV Files](http://bconnelly.net/working-with-csvs-on-the-command-line/#working-with-gzip-compressed-csv-files)
> - [A Quick Overview of the Commands Used in this Cookbook](http://bconnelly.net/working-with-csvs-on-the-command-line/#a-quick-overview-of-the-commands-used-in-this-cookbook)
> 
> 

## A Quick Introduction to Pipes and Redirection

>[!quote]
>Most of the commands available on the command line were developed with the same goals: to do a single job and to do it well. The real power of the command line comes from stringing these programs together to perform more complex tasks. By knowing just a handful of commands, just about anything is possible.

### Writing Output to a File with Output Redirection

>[!quote]
>By default, most command line tools give their results by **printing them to the screen**. This might be ok when doing some calculations, but it’s not so useful if you’re transforming files (like CSVs) and intend to save them, share them, or use the results in some other software.
>
>With **output redirection**, you can tell the command line to write the *output of one or more commands* to *a file* instead of printing it to the screen. To do this, just add the `>` character and the name of the file where you want the output to be stored to the end of the command. If the output file doesn’t already exist, `>` will create that file. If that file exists, `>` will replace its contents with the new output. If you’d rather add the output of your commands to an existing file, you can use `>` instead.


>[!example]
>For example, the following command (which will be described in more detail in the first recipe) will print all of the lines of the file `input.csv` that do not begin with a `#` character:
> ```bash
> grep -v "^#" input.csv
> ```
>- Instead, to save those results to a file named `output.csv`, we could use *output rediraction* and would run:
> ```bash
> grep -v "^#" input.csv > output.csv
> ```
>- If `output.csv` *already existed*, its contents would be **replaced**. If we instead wanted to add the output of the current command to `output.csv`, we’d do:
> ```bash
> grep -v "^#" input.csv >> output.csv
> ```

- [[Save Standard Output and Standard Error to files]]

### Connecting Programs with Pipes

>[!important]
>**Pipes**, denoted with the `|` character, allow the output of one program to be sent as input to another program. This saves you from having to first save the output of the first program to a file, and then start the second program using that file as input. You can imagine that a workflow with many steps could generate a lot of intermediate files and require a lot of concentration to see things through from start to finish.

>[!example]
>Using our previous example once again:
> ```bash
> grep -v "^#" input.csv
> ```
> Prints all of the lines of `input.csv` that do not contain the `#` character. 


>[!info]
>- The `grep` program **searches for patterns** within files (see [A Quick Overview of the Commands Used in this Cookbook](http://bconnelly.net/working-with-csvs-on-the-command-line/#a-quick-overview-of-the-commands-used-in-this-cookbook)). Here, we’re using it **in reverse** and *finding where a pattern does not exist*. 
>- If we wanted to *count the number of non-commented lines* (i.e., those with `#`) in `input.csv`, we could use grep to strip out lines with `#`, and use a pipe to send the results to the `wc` program, which can count the number of lines in its input when used with the `-l` argument:
> ```bash
> grep -v "^#" input.csv | wc -l
> ```
>Pipes are used *extensively* in the recipes that follow. If you’re still not quite comfortable with how they work, try executing the commands in the recipes one by one to see what the output of each part is. Then try to visualize how they all come together.

## Cleaning Up CSV Files

### Removing Comments

>[!quote]
>Comments are additional information stored in the file that are not a part of the actual data set, but that either describe the data set or provide relevant information (_metadata_). Comments could include things like the name of the person who gathered the data, the date on which measurements were made, the equipment used, or notes about a particular record. Typically, comments occur on their own line and begin with a `#` sign as demonstrated below:
```
Temperature,Row,Column,Luminescence
# Luminescence of evolved strain
# Collected by Harvey I. Vibrio - 2012/06/27

26.3,0,0,7444.945
26.3,0,1,4845.375
26.3,0,2,4056.362
# Look at this luminescence!!!
26.3,0,3,4883.137
26.3,0,4,3593.289
26.3,0,5,2645.281
26.3,1,2,10507.588
```


>[!info]
>Despite their common use, comments are not supported by all software and can occasionally cause problems when importing data. Fortunately, comments can quickly be stripped from a file using the `grep` command. 


>[!example]
>- The following command strips out all lines that begin with the `#` character from a file named `input.csv`:
> ```bash
> grep -v "^#" input.csv
> ```
> This command will print all the lines of `input.csv` that do not begin with `#`. The `^` character means the beginning of a line. 
> - To save this output as a file, we can redirect the output of `grep` to a new file called `input-nocomments.csv`:
> ```bash
> grep -v "^#" input.csv > input-nocomments.csv
> ```
>Now, `input-nocomments.csv` can be imported into programs that do not support comments.

### Removing Headers

>[!info]
>Headers are commonly used to name each column. They appear as a comma-separated list of column names at the top of the file. Sometimes, it is beneficial to **remove headers from a CSV file** when **merging multiple files** (see [Combining Rows from Two or More CSVs](http://bconnelly.net/working-with-csvs-on-the-command-line/#combining-rows-from-two-or-more-csvs) below) or when the software you’re using to import the data is finicky. 


>[!example]
>For example, R expects the header to be the first line of a file and cannot be preceded by comments. Assuming that the header is on the first line of `input.csv`, we can remove it with the `cat` and `sed` commands:
> ```bash
> cat input.csv | sed "1 d"
> ```
>>[!info]
>>This uses the Unix **pipe** (`|`) symbol to connect the output of the `cat` program, which just prints the contents of the file, to the `sed` program, which we use to delete the first line. The `1` can be replaced in the parameters to `sed` to allow a different number of lines to be skipped. As before, the results of this command are printed. 
>To save these results as a new file named `noheader.csv`, the output can be redirected:
> ```bash
> cat input.csv | sed "1 d" > noheader.csv
> ```


>[!example]
>If our input file has *comments before the header line*, this command won’t quite have the effect that we want, because `sed` blindly removes the first line of the file. Through the power and beauty of the command line, however, we can combine our comment stripping ability with our line chopping ability:
> ```bash
> cat input.csv |  grep  -v "^#"  | sed "1 d" > onlydata.csv
> ```
>This command uses `cat` to send the contents of the file to `grep`, which only prints out lines that do not begin with `#`. The output goes to `sed`, which removes the first line of the non-commented data. Finally, the results of this string of operations are placed in a new file named `onlydata.csv`.


### Changing Delimiters

>[!info]
>You can easily change the delimiter of a file using the `tr` command. 

>[!example]
>- To convert a **tab-separated values file** named `input.tsv` to a **CSV file** named `input.csv`:
> ```bash
> cat input.tsv |  tr  "\t"  "," >  input.csv
> ```
>The two arguments given in this command indicate the character to change `"\t"` (a tab), and the character to change it to `","` (a comma). 
>
>- Similarly, we can **convert a CSV file to a TSV file** by reversing the arguments:
> ```bash
> cat input.csv |  tr  ","  "\t" >  input.tsv
> ```

>[!quote]
>Sometimes the comma character is present in records in CSV file, such as when an address is a record. When this is the case, it is common to place the whole value within quotes to differentiate between a comma in a value and a comma used as a delimiter. The commands above aren't smart enough to know whether a comma is within a quote or not (or whether it's part of a comment -- see [Removing Comments](#Removing_Comments)). Because of this, commas enclosed within quotes would still be translated to tabs in the previous example. If you are dealing with CSVs where commas are included in values, consider using tabs as delimiter and/or using more complex scripts to count columns.

## Getting Information about the Data Set

>[!quote]
>Before working with a data set, you’d sometimes like to get a sense of how big it is and the types of values that it stores. This section provides a few ways of doing this.

### Taking a Peek at the Data Set

>[!info]
>In the previous recipe, we removed comments and the header from a CSV file. We did so, because we knew beforehand that they existed in the data set. If we’re not familiar with the file, we can usually determine whether or not there are headers or comments by looking at the first few lines of the file. Instead of opening the file, which could be quite large, with a text editor, we can quickly use the `head` command:
> ```bash
> head input.csv
> ```
> This command will display the first *10 lines* of `input.csv`. To see more or fewer lines, we can specify the number using the `-n` argument:
> ```bash
> head -n 7 input.csv
> ```
> This should give us an idea whether or not there’s a header in the file and if there are comments within the first few lines. 

>[!example]
> - If we want to search the whole file for comments, we can use grep:
> ```bash
> grep "#" input.csv
> ```
>    Which prints each line in `input.csv` that contains the `#` character. 
> 
> - If we instead want to know the number of comments that occur in the file, we can send the output to the `wc` command, which can count the number of lines in the output of `grep` when used with the `-l` argument:
> 
> ```bash
> grep "#" input.csv | wc -l 
> ```
>   If the output from this command is 0, then we know that `input.csv` contains no comments.

### Determining the Number of Rows

>[!info]
>The `wc` command lists the number of lines in a file when the `-l` argument is given.
> ```bash
> wc -l input.csv
> ```
> It does so indiscriminately, so its count will include headers and comments. 

>[!example]
> Using previous recipes, though, we can strip these things from the file before counting the number of lines.
> ```bash
> cat input.csv | grep -v "^#" | sed "1 d" | wc -l
> ```
> This command will print out the `input.csv` file, send it to `grep`, which strips out lines containing `#`. The output of this is sent to `sed`, which strips out the header on the first line (assuming we have one—see previous recipe). The result of all this is then sent to `wc`, which counts and prints the number of lines, each of which is presumably a data record.


### Determining the Number of Columns

>[!example]
> - Similarly, we can determine the number of columns in the data set by looking at the non-comment lines:
> ```bash
> cat input.csv | grep -v "^#" | awk "{print NF}" FS=,
> ```
>  This command uses `grep` to strip out commented rows, and sends the remaining rows to `awk`, which reports *the number of comma-separated fields* (the `FS` argument) in each line. 
>- We can send these results to the `uniq` command to only output the unique numbers of columns present in the file:
> ```bash
> cat input.csv | grep -v "^#" | awk "{print NF}" FS=, | uniq
> ```

>[!quote]
>Typically, all rows in a CSV file contain the same number of records. In that case, the command will return one number. If more than one number is returned, there is some variation in the number of records per line in the file, which could cause other problems.
>
>Sometimes the comma character is present in records in CSV file, such as when an address is a record or when using a comma as a decimal mark. In these instances, it is common to place the whole value within quotes. The commands above aren't smart enough to know whether a comma is within a quote or not. If you are dealing with CSVs where commas are included in values, consider switching your delimiter to tabs and/or using more capable scripts to count columns.


## Combining CSVs

The following recipes deal with combining data from two or more CSV files.

### Combining Rows from Two or More CSVs

>[!info]
>If some of our records are stored in one file, say `input1.csv`, and other records are stored in one or more others, we can combine these files (vertically) into one large data file called `combined.csv` using `cat`:
> ```bash
> cat input1.csv input2.csv input3.csv > combined.csv
> ```

- [[Concatenate multiple files into one]]

>[!info]
>It is important to note that each of the **files should contain the same number of columns** and have those columns occurring *in the same order*. Recipes for extracting specific columns in order to rearrange them are included later.

>[!example]
>If each of the input files has a header, each of those header lines will be copied into `combined.csv`. The easiest way to deal with this is to strip the header line from each file as we combine them:
> ```bash
> cat input1.csv > combined.csv
> cat input2.csv | sed "1 d" >> combined.csv
> cat input3.csv | sed "1 d" >> combined.csv
> ```
>You may have noticed that we copied `input1.csv` as-is into `combined.csv`. By doing this, we’re using the header from the first file as the header for our new combined file. The remaining lines use `sed` to filter out the first line before adding the contents of `input2.csv` and `input3.csv` to `combined.csv` (note the use of `>>`, which appends the additional data to the output file). The file that results from these commands will contain the header and data from `input1.csv` and just the data from `input2.csv` and `input3.csv`.

### Combining Columns from Multiple CSVs

>[!example]
>If the fields of your data are spread across multiple files, these can be combined (horizontally) using `paste`:
> ```bash
> paste -d , input1.csv input2.csv > combined.csv
> ```
> Here, the `-d ,` argument says that the contents from `input1.csv` and `input2.csv` will be separated (**d**elimited) by a comma. By default, paste will separate columns using a tab.

>[!info]
>It is important to note here that doing this *assumes that the order of the data in each input file is the same* and that the record(s) in row 8 of `input1.csv` correspond to the record(s) in row 8 of `input2.csv`.
>
>If you’re interested in extracting specific columns from your input file(s), see the recipe for [Extracting Columns](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-columns).

## Extracting Data Subsets

### Extracting Specific Row Numbers from CSVs

>[!info]
>Data entries in CSV files can be extracted either by specific line numbers or by matching some criteria. The former is more straightforward and can be done in a number of ways depending on which lines you’re interested in.

>[!example]
>If we’re interested in the *first* few rows of data, we can use the `head` command. For example, to extract the first 13 lines from `input.csv` and save the results to `first13.csv`, we could execute:
> ```bash
> head -n 13 input.csv > first13.csv
> ```


>[!example]
>To make sure we’re extracting *only data* and **not headers and comments**, we could **first strip** these following the [Removing Headers](http://bconnelly.net/working-with-csvs-on-the-command-line/#removing-headers) recipe:
> ```bash
> cat input.csv | grep -v "^#"  | sed "1 d" | head -n 13 > first13.csv
> ```


>[!example]
> Similarly, if we’re interested in extracting the *last* 8 rows from the input file, we could use the `tail` command:
> ```bash
> tail -n 8 input.csv > last8.csv
> ```


>[!example]
> As with the previous example, we may want to first **strip out any comments**. When we take *rows from the end*, we’re not getting the header. One easy way to do this would be to **first extract the header** from the input file using `head`, and then **pull out the last 8 columns**:
> ```bash
> head -n 1 input.csv > last8.csv
> tail -n 8 input.csv >> last8.csv
> ```


>[!example]
> As we’ve seen before, the `>` creates a new file (or overwrites an existing one) named `last8.csv`, and writes the output of `head` to it. The `>>` then appends the results of `tail` to this file. If you’d like to do these two steps in one line (that still contains two commands), these lines can be combined with `;`:
> ```bash
> head -n 1 input.csv > last8.csv ; tail -n 8 input.csv >> last8.csv
> ```
> 
> If for some reason you know the specific line numbers of interest, you can carve out those lines using `sed`. For example, to extract lines 10 through 14:
> ```bash
> sed -n "10,14 p" input.csv
> ```


### Extracting Rows Based on Some Value

>[!example]
>The other case is when we’re interested in **selecting rows** by *a certain value*. For example, we may have phone book stored as a CSV, where each row contains the name of a person or business and their number. If we wanted to create a CSV that contains all of the places (or people!) with _Pizza_ in their name, we could use `grep` to find all rows in the file containing that word and save the results to a new phone book of pizza places named `pizza.csv`:
> ```bash
> grep "pizza" input.csv > pizza.csv
> ```

>[!example]
>As with the previous example, `pizza.csv` will not contain headers, so we can use `head`:
> ```bash
> head -n 1 input.csv > pizza.csv 
> grep "pizza" input.csv >> pizza.csv
> ```
>- Note that `pizza.csv` will also contain any comments that include the word _pizza_, so you may want to first strip comments from your input. 
>- Note that `grep` is case sensitive, so it will match records containing _pizza_ but not ones containing _pizza_. 
>- We can make `grep` case insensitive by adding the `-i` argument:
> ```bash
> grep -i "pizza" input.csv >> pizza.csv
> ```
> 
>If you’re interested in extracting rows based on criteria other than matching some specified text, such as rows containing some value greater than a number of interest, I’d recommend *moving away from command line tools* and creating a script in something like Python or R.

### Extracting Columns

>[!example]
>**Specific columns** can also be easily extracted from CSVs. For example, if we wanted to extract columns 2, 4, 5, and 6 from `input.csv`:
> ```bash
> cut -d , -f 2,4-6 input.csv
> ```
>Here, the `-d ,` tells `cut` that columns are separated by commas, and `-f 2,4-6` tells it to extract column 2 and columns 4-6. The `-f` argument can take a single column number or a comma-separated list of numbers and ranges.

## Working with Compressed CSV Files

>[!quote]
>If our data set gets very large, we can compress the CSV file using a file compression tool such as `bzip2` or `gzip` to shrink the file size (sometimes dramatically). With slight modification, any of the commands shown in this cookbook can be used with compressed CSV files. Additionally, tools such as Python and R have `bzip2` and `gzip` support, so they can read and write these compressed CSV files as well.

### Compressing CSV Files with bzip2

>[!info]
>- `bzip2` is an open source compression tool available on most Linux and OS X machines. To compress your input file, run:
> ```bash
> bzip2 input.csv
> ```
> - This will produce a file named `input.csv.bz2`. If you should ever need to uncompress this file, use the `--decompress` or `-d` arguments:
> ```bash
> bzip2 -d input.csv.bz2
> ```


### Working with bzip2-Compressed CSV Files

>[!info]
>If you look at `input.csv.bz2`, it will look like an unintelligible chunk of characters. This is exactly how the file will look to any of the other utilities we’ve used in this cookbook. These utilities expect to work with plain text, so they usually can’t handle compressed data. Fortunately, we can easily give these tools the uncompressed data without actually uncompressing the file. To do so, we’ll use the `bzcat` command, which prints out the uncompressed contents of the file, and then use pipes to send that output to the right tools. 

>[!example]
>For example, if we want to extract the third column of a compressed CSV file (see [Extracting Columns](http://bconnelly.net/working-with-csvs-on-the-command-line/#extracting-columns)) and save the results to `col3.csv`, we could run:
> ```bash
> bzcat input.csv.bz2 | cut -d , -f 3 > col3.csv
> ```
>
>Since we’re all about dealing with compressed CSVs, we could also save the results to a bzipped file after passing the results through the `bzip2` command:
> ```bash
> bzcat input.csv.bz2 | cut -d , -f 3 | bzip2 > col3.csv.bz2
> ```


### Compressing CSV Files with gzip

>[!example]
>Some older machines will not have `bzip2` installed. These machines likely have another open source compression tool called `gzip` installed. Similarly to `bzip2`, files can be compressed by passing them to the `gzip` command:
> ```bash
> gzip input.csv
> ```
> which produces `input.csv.gz`.
> 
>To uncompress this file, just use the `gunzip` command:
> ```bash
> gunzip input.csv.gz
> ```


### Working with gzip-Compressed CSV Files

>[!quote]
>Working with gzip-compressed CSV files is the same as described in [Working with bzip2-Compressed CSV Files](http://bconnelly.net/working-with-csvs-on-the-command-line/#working-with-bzip2-compressed-csv-files) with the exception of using the `gzcat` command instead of `bzcat`. If you cannot find `gzcat` on the machine, try `zcat`.

## A Quick Overview of the Commands Used in this Cookbook

>[!important]
>This section provides a quick description of each of the commands used and a link to their man page (manual).
> - `awk`: AWK is a programming language (and command) that is great for processing text ([man page](http://www.linuxmanpages.com/man1/awk.1.php))
> - `cat`: con**cat**enates and prints files ([man page](http://www.linuxmanpages.com/man1/cat.1.php))
> - `cut`: removes specific bytes, characters, or fields from files ([man page](http://www.linuxmanpages.com/man1/cut.1.php))
> - `grep`: finds lines matching (or not matching) a given pattern ([man page](http://www.linuxmanpages.com/man1/grep.1.php))
> - `head`: outputs the first part of a file ([man page](http://www.linuxmanpages.com/man1/head.1.php))
> - `sed`: perform simple manipulations to text in a file ([man page](http://www.linuxmanpages.com/man1/sed.1.php))
> - `tail`: outputs the end of a file ([man page](http://www.linuxmanpages.com/man1/tail.1.php))
> - `tr`: changes (**tr**anslates) characters within a file ([man page](http://www.linuxmanpages.com/man1/tr.1.php))
> - `wc`: counts the number of characters, words, and lines in a file ([man page](http://www.linuxmanpages.com/man1/wc.1.php))

__ Due to some diversity in the Unix world, the arguments for some commands may be slightly different from machine to machine.



-----------
##  Recommended Notes

[[AWK command in Unix or Linux with examples]]

- **Introduction to Unix (also Linux, OS X, etc.) and The Command Line**
	- [UNIX Tutorial for Beginners](http://www.ee.surrey.ac.uk/Teaching/Unix/)

- **Software Support for CSV**
	- The Python [CSV module](http://docs.python.org/2/library/csv.html)
	- Reading CSV files in R with [read.table](http://stat.ethz.ch/R-manual/R-devel/library/utils/html/read.table.html) (also see the [readr](https://cran.r-project.org/web/packages/readr/) package)
	- CSV in [Mathematica](http://reference.wolfram.com/mathematica/ref/format/CSV.html)
	- CSV in [Matlab](http://www.mathworks.com/help/matlab/ref/csvread.html)
	- CSV in [Excel](https://office.microsoft.com/en-us/excel-help/import-or-export-text-txt-or-csv-files-HP010099725.aspx)

- **CSV Format**
	- Wikipedia pages for [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) and [TSV](https://en.wikipedia.org/wiki/Tab-separated_values)
	- [RFC 4180](https://tools.ietf.org/html/rfc4180), which is the unofficial standard for CSV.
	- [BEACONToolkit CSV](https://github.com/briandconnelly/BEACONToolkit/blob/master/csv/doc/csv.md) [Luis Zaman](http://luis.labfab.cc/) and I introduced CSV and how to read/write CSV from Excel, Python, R, and the command line as part of our [BEACONToolkit](https://github.com/briandconnelly/BEACONToolkit) seminar


----------
##  Citations

- Blog
	- [Working with CSVs on the Command Line]([http://bconnelly.net/working-with-csvs-on-the-command-line/](http://bconnelly.net/working-with-csvs-on-the-command-line/))
- *code source*:
- *code package link*




