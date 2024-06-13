---
tags:
  - code
  - code_snippet
  - algorithm/search
  - leetcode/algorithm
  - c_plus
keywords: 
topics:
  - leetcode
  - search
language: c++
date of note: 2024-03-23
---

## Code Snippet Summary

>[!todo] Problem Statement
>Write a function to find the **longest common prefix** string amongst an array of strings.

## Code

>[!important] Highlight
>- This is a **Search** problem.
>- Set two search index *i* and *j*,  where *i* points to the position in a string, and *j* points to a string in the array of strings
>- **The longest common prefix** is defined as 
>  $$
>   \sup\left\{i \le n: s_{j}[0:i] == s_{k}[0:i],\; \forall j,k = 1,\ldots, m\right\}
> $$
> - pointer *i* means that all prefix until position *i* are common prefix among all strings in the array. 
> - This search requires $\mathcal{O}(nm)$ time complexity, where $m$ is the number of strings, $n$ is the minimum length of string in the array
 


```c++

 string longestCommonPrefix(vector<string>& strs) {

        if(strs.empty()) return "";
        int i = 0, j=0, n = strs.size(), m=strs[0].size();
        string res;
        res.clear();
        for(i=0; i<m; i++){
            char cur = strs[0][i];
            for(j=1; j<n; j++){
                int strsize = strs[j].size();
                if(i>= strsize || cur != strs[j][i]){
                    return res;
                }
            }
            res.push_back(cur);
        }
        return res;
    }
```




-----------
##  Recommended Notes

