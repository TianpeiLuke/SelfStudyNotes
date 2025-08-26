---
tags:
  - project
  - design
  - information_retrieval/retrieval_augmentation
  - gemini_llm
aliases:
date of note: 2025-08-22
---

```
i am looking for material that built a RAG in AWS, with my knowledge base in https://github.com/TianpeiLuke/cursus/tree/main/slipbox; the purpose is to assist the agentic workflow i designed in https://github.com/TianpeiLuke/cursus/blob/main/slipbox/3_llm_developer/developer_prompt_templates/README.md

  

provide instructions on how to build such RAG system
```

Of course, I can help with that. Here are the instructions on how to build a RAG system on AWS.

### **High-Level Architecture**

A typical RAG architecture on AWS involves several key services working together. Here's a conceptual overview:

1. **Data Ingestion**: Your knowledge base from the GitHub repository will be ingested into a storage service.
    
2. **Data Processing and Embedding**: The raw data (your markdown files) will be processed, chunked into smaller pieces, and then converted into vector embeddings using an embedding model.
    
3. **Vector Store**: These vector embeddings will be stored in a specialized database that allows for efficient similarity searches.
    
4. **Retrieval**: When a user query comes in, it will also be converted into a vector embedding. The vector store is then queried to find the most relevant document chunks based on the similarity between the query embedding and the stored document embeddings.
    
5. **Generation**: The retrieved document chunks are then combined with the original user query and passed as context to a large language model (LLM). The LLM uses this context to generate a more accurate and relevant response.
    

---

### **Step-by-Step Instructions**

Here is a step-by-step guide to building your RAG system on AWS:

#### **1. Data Ingestion: Getting Your Knowledge Base into AWS**

- **Source**: Your GitHub repository `https://github.com/TianpeiLuke/cursus/tree/main/slipbox`.
    
- **Destination**: **Amazon S3 (Simple Storage Service)** is the ideal place to store your raw knowledge base files.
    

**Action**:

1. **Clone your GitHub repository to your local machine**:
    
    Bash
    
    ```
    git clone https://github.com/TianpeiLuke/cursus.git
    ```
    
2. **Create an S3 bucket** in your AWS account.
    
3. **Upload the contents of the `slipbox` directory** to your S3 bucket. You can do this via the AWS Management Console or the AWS CLI:
    
    Bash
    
    ```
    aws s3 sync cursus/slipbox/ s3://your-rag-knowledge-base-bucket/
    ```
    

#### **2. Data Processing and Embedding**

- **Services**: **AWS Lambda** for processing and **Amazon Bedrock** for embeddings.
    

**Action**:

1. **Set up an AWS Lambda function** that is triggered whenever a new file is uploaded to your S3 bucket.
    
2. **In the Lambda function**:
    
    - Read the content of the uploaded markdown file from S3.
        
    - **Chunk the text** into smaller, manageable pieces. A common approach is to split by paragraphs or a fixed number of characters with some overlap.
        
    - **Use an embedding model** from Amazon Bedrock (e.g., Amazon Titan Embeddings) to convert each text chunk into a vector embedding.
        

#### **3. Vector Store: Storing Your Embeddings**

- **Services**: You have several options here. For a serverless and easy-to-manage solution, **Amazon OpenSearch Serverless** or **Amazon RDS for PostgreSQL with the `pgvector` extension** are great choices. For a fully managed RAG experience, you can use **Knowledge Bases for Amazon Bedrock**.
    

**Action (using OpenSearch Serverless)**:

1. **Create an OpenSearch Serverless collection**.
    
2. **Configure the collection** with a vector index to store your embeddings.
    
3. **Modify your Lambda function** from the previous step to write the generated embeddings (along with the original text chunks) to your OpenSearch Serverless index.
    

#### **4. Retrieval and Generation: The RAG Core**

- **Services**: **Amazon API Gateway**, **AWS Lambda**, and **Amazon Bedrock**.
    

**Action**:

1. **Create another Lambda function** that will serve as your RAG's backend logic. This function will be triggered by an API call.
    
2. **Set up an API Gateway endpoint** that routes user queries to this Lambda function.
    
3. **In the Lambda function**:
    
    - **Receive the user query** from the API Gateway event.
        
    - **Convert the user query into a vector embedding** using the same Amazon Bedrock embedding model you used for your documents.
        
    - **Query your OpenSearch Serverless index** with the query embedding to find the most similar (i.e., most relevant) document chunks.
        
    - **Construct a prompt** for the LLM. This prompt should include the original user query and the retrieved text chunks as context.
        
    - **Invoke an LLM** from Amazon Bedrock (e.g., Anthropic's Claude) with the constructed prompt.
        
    - **Return the LLM's generated response** to the user through the API Gateway.
        

This video provides a great overview of how to interact with your GitHub repository via RAG: Interacting with your code using AI








-----------
##  Recommended Notes