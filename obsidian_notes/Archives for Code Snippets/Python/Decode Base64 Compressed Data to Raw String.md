---
tags:
  - code
  - code_snippet
  - python/string
  - python/compress
keywords: 
topics: 
language: python
date of note: 2025-03-14
---

## Code Snippet Summary

>[!important]
>Suppose that the *encoding process* for output is given by
>-  *compress* the text in `.gzip`
>-  *encode* compressed text in `base64`
>  
>Run the *decoding process* as part of input transformation as
>- *decode* the input in `base64`
>- *uncompress* the decoded text in `gzip`


## Code

```python
import base64
import gzip
import json
```

```python
def extractPayload(response):
    initial = json.loads(response)
    payload = json.loads(initial["string"])
    responses = json.loads(payload["payload"])

    if responses["errorFlag"] == True:
        print("Error in TGPT response: ", responses["errorMessage"])
        raise Exception("Error in TGPT response")
    else:
        return responses["answers"]


def base64Decode(payload):
    return base64.b64decode(payload)

def uncompress(payload):
    return gzip.decompress(payload)

if __name__ == "__main__":
    full_response = json.dumps({"string":"{\"payload\": \"{\\\"errorFlag\\\": false, \\\"errorMessage\\\": \\\"\\\", \\\"answers\\\": \\\"H4sIAGZKy2cC/21STW/bMAz9K4TPbrBcdynQezdgCbBDERisREfCZMkVqSZp0f9eSl6aptvBgsWv9/ieHl67p0IsPsXB22P3Hb718BHSa7cp04TZvxCII/DMhWCiWNNkwccWvtvcd9qHkQ+Ua9dWgzShD2BSzsRzipaiITggw5RYwqk1MoVAGaTixT0slUwMklr+sZwor2B7/gXkPwqr2HAmCfiYirTqOSdbjIAlUWju4eC8cZ+BzlSsArSxeaEUE6CRggFStlo3BzQVJwM7P89kV3W/kg7DjBknEsqsez7sNJoJ+YtWtmGaFEWVgjS266IHHY3DuNd9kNsmygltXV5cTmXvLrW86t56+Meh9ReHfjsUNab1LVxgVOIf8lUtRx8WA01AP91em/Xj5xb0+/X/FTvrx3FofcMyfmDJ3ScS10kf5yK1ZKiz1t21RBcnIz3reXlKGE/iqg6Ln6guBjyR7dWcePPXhh4CCvXVmEnfYi1vhqlSu3erAn50zAIAAA==\\\"}\"}"})
    payload = extractPayload(full_response)
    decoded = uncompress(base64Decode(payload))
    parsed = json.loads(decoded)

    print("Full Response is: ", full_response)
    print("Payload is: ", payload)
    print("Decoded: ", decoded)
    print("Parsed: \n", json.dumps(parsed, indent=4))
```




-----------
##  Recommended Notes

