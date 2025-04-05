---
tags:
  - code
  - code_snippet
  - c_plusplus
  - c_plusplus_11
keywords: 
topics: 
language: c++
date of note: 2024-04-24
---

## Code Snippet Summary

>[!important]
>Use *Lambda Expression* in C++ (C++ 11 above) to define inline functions


## Code

### Lambda Expression as Functor

- Lambda expressions without an explicit template parameter list (possibly non-generic)

```
[captures] front-attr ﻿(optional) (params) specs ﻿(optional) exception ﻿(optional)  
back-attr ﻿(optional) trailing-type ﻿(optional) requires ﻿(optional) { body }
```

```
[captures] { body }
```

```
[captures] front-attr ﻿(optional) trailing-type ﻿(optional) { body }
```


- `captures`: A comma-separated list of zero or more [captures](https://en.cppreference.com/w/cpp/language/lambda#Lambda_capture), **optionally** beginning with a capture-default. 
	- See [below](https://en.cppreference.com/w/cpp/language/lambda#Lambda_capture) for the detailed description of captures.
	- A lambda expression can use a variable **without capturing** it if the variable
		- is a *non-local variable* or has *static or thread local* [storage duration](https://en.cppreference.com/w/cpp/language/storage_duration "cpp/language/storage duration") (in which case the variable cannot be captured), or
		- is a *reference* that has been initialized with a [constant expression](https://en.cppreference.com/w/cpp/language/constant_expression#Constant_expression "cpp/language/constant expression").
	- A lambda expression can read the value of a variable **without capturing** it if the variable
		- has *const non-volatile integral* or *enumeration type* and has been initialized with a [constant expression](https://en.cppreference.com/w/cpp/language/constant_expression#Constant_expression "cpp/language/constant expression"), or 
		- is *constexpr* and has *no mutable members*.
		  
- `front-attr`: An [attribute specifier sequence](https://en.cppreference.com/w/cpp/language/attributes "cpp/language/attributes") applies to operator() of the *closure type*.
- `params`: The [parameter list](https://en.cppreference.com/w/cpp/language/function#Parameter_list "cpp/language/function") of operator() of the *closure type*.
- `trailing-type`: `->` ret, where ret specifies the *return type*.
- `body`: The function body.


>[!example]
> ```cpp
> // generic lambda, operator() is a template with two parameters
> auto glambda = [](auto a, auto&& b) { return a < b; };
> ```


>[!quote]
>Lambda offers a simpler way to write a **functor**. It is a syntactic sugar for an anonymous functor. It reduces the boilerplate that we need to write in a functor.
>- [C++ Basics: Understanding Lambda](https://builtin.com/software-engineering-perspectives/c-plus-plus-lambda)


>[!example]
> ```cpp
>   auto plus = [data=1](const int value)
>     {
>         return value + data;
>     };
> ```

### C++ Lambda Callback Function




-----------
##  Recommended Notes

- [Lambda expressions (since C++11)](https://en.cppreference.com/w/cpp/language/lambda)

- Stack Overflow:
	- [What is a lambda expression, and when should I use one?](https://stackoverflow.com/questions/7627098/what-is-a-lambda-expression-and-when-should-i-use-one)

- [C++ Basics: Understanding Lambda](https://builtin.com/software-engineering-perspectives/c-plus-plus-lambda)