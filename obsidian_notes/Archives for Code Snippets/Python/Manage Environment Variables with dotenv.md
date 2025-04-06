---
tags:
  - code
  - code_snippet
  - python/dotenv
keywords: 
topics: 
language: python
date of note: 2025-04-06
---

## Code Snippet Summary

>[!important]
>Use `dotenv` to manage the environment variable
>- Useful when calling LLM from API (e.g. OPENAI ChatGPT)


## Code

```python
from dotenv import load_dotenv
```

- The `dotenv` package is used for managing environment variables in your project.
- The `load_dotenv` function reads a file (usually named `.env`) and loads the environment variables defined in that file into your system's environment (accessible via `os.environ`).


```python
from dotenv import load_dotenv
import os

load_dotenv()  # Loads the .env file into the environment variables

# Now you can access environment variables like this:
api_key = os.getenv('API_KEY')

```

- This ensures that when your program starts, it has access to all the configuration settings defined in your `.env` file.

- Overall, this single import statement is a key part of setting up a Python application to manage its configuration in a clean and secure way.


### Why Use It?

- **Separation of Concerns:** It helps separate configuration details (like database URLs, secret keys, API tokens) from your application code.
    
- **Security:** By keeping sensitive information in a separate file that isn’t committed to version control, you reduce the risk of exposing credentials.
    
- **Portability:** You can easily switch environments (development, testing, production) by changing the environment variable values in the `.env` file without altering your code.


-----------
##  Recommended Notes

