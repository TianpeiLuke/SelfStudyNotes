---
tags:
  - code
  - code_snippet
  - latex/code
keywords: 
topics: 
language: latex
date of note: 2024-04-14
---

## Code Snippet Summary

>[!important]
>Write code inside a paper. 


## Code

### Use `verbatim`

```latex
\begin{verbatim}
Your Code Here
\end{verbatim}
```


###  Use `fancyvrb` and `fvextra` packages

- Can break lines when the code is too wide.

```latex
\usepackage{fancyvrb,fvextra}
```

```latex
\begin{Verbatim}[breaklines]
Your Code
\end{Verbatim}
```


> [!example]
> ```latex
> def lf_rule_msg_entry(df):
>     if df['risk_value_entry_point'] >= 0.3:
>         return REVERSAL
>     else:
>         return ABSTAIN
> ```
> 
> 

### Use `minted` to have syntax highlighting

```latex
\usepackage{minted}
```

```latex
\begin{minted}[breaklines]{language}
Your Code
\end{minted}
```

- You can choose `language` to use under `minted`
- `minted` requires the installation of **additional software**, `Pygments`.

### `listings` package

```latex
\usepackage{listings}
```

- `lstlisting` environment

```latex
\begin{lstlisting}[breaklines]
  Long user text
\end{lstlisting}
```

- Define style with `breaklines=true`
```latex
\lstset{
basicstyle=\small\ttfamily,
columns=flexible,
breaklines=true
}
```

```latex
\begin{lstlisting}
Your Code
\end{lstlisting}
```



-----------
##  Recommended Notes

- `fancyvrb` package [CTAN reference](https://ctan.org/pkg/fancyvrb)
	- Flexible handling of verbatim text including: 
		- verbatim commands in footnotes; 
		- a variety of verbatim environments with many parameters; 
		- ability to define new customized verbatim environments; 
		- save and restore verbatim text and environments; 
		- write and read files in verbatim mode; 
		- build “example” environments (showing both result and verbatim source).
- `fvextra` package [CTAN reference](https://ctan.org/pkg/fvextra)
	- provides several extensions to `fancyvrb`, including 
		- automatic line breaking and improved math mode. 
		- It also patches some `fancyvrb` internals. 
		- Parts of `fvextra` were originally developed as part of `pythontex` and `minted`.
- `minted` package [CTAN reference](http://www.ctan.org/pkg/minted)
	- The package that facilitates expressive syntax highlighting in LaTeX using the powerful `Pygments` library. 
	- The package also provides options to customize the highlighted source code output using [fancyvrb](https://ctan.org/pkg/fancyvrb).
- `listings` package [CTAN reference](http://www.ctan.org/pkg/listings)

- Tex Stack Exchange
	- [Verbatim with Wrapping?](https://tex.stackexchange.com/questions/510316/verbatim-with-wrapping)
	- [Verbatim environment that can break long lines?](https://tex.stackexchange.com/questions/14342/verbatim-environment-that-can-break-long-lines)
	- [Automatically wrap the text in verbatim \[duplicate\]](https://tex.stackexchange.com/questions/121601/automatically-wrap-the-text-in-verbatim)