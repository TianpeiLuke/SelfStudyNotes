---
tags:
  - code
  - code_snippet
  - latex/tables
keywords: 
topics: 
language: latex
date of note: 2024-04-08
---

## Code Snippet Summary

>[!important]
>- Create Table in Latex
>- Use `tabularx` package to adjust column width automatically

## Code

### Use `booktabs` package

```latex
\usepackage{booktabs}       % professional-quality tables
```

- `booktabs`  package allows for typesetting high-quality, professional tables: see [reference](https://www.ctan.org/pkg/booktabs)

```latex
\begin{table}
  \caption{Sample table title}
  \label{sample-table}
  \centering
  \begin{tabular}{lll}
    \toprule
    \multicolumn{2}{c}{Part}                   \\
    \cmidrule(r){1-2}
    Name     & Description     & Size ($\mu$m) \\
    \midrule
    Dendrite & Input terminal  & $\sim$100     \\
    Axon     & Output terminal & $\sim$10      \\
    Soma     & Cell body       & up to $10^6$  \\
    \bottomrule
  \end{tabular}
\end{table}
```


- `\begin{table}[position] ... \end{table}`:

- `\begin{tabular}{col1_width_centering}{..} ... \hline ... \end{tabular}`:

- `\multicolumn{num_columns}{config}{entity}`:

- `\toprule`, 
- `\cmidrule`, 
- `\midrule`, 
- `\bottomrule`


>[!info]
>- All tables must be *centered*, neat, clean and legible.  
>- The table number and title always appear *before* the table. 
>- Place *one line space* *before* the table title, *one line space* *after* the table title, and *one line space after the table*. 
>- The table title must be *lower case* (except for first word and proper nouns); 
>- tables are numbered consecutively.
>- Note that publication-quality tables **do not contain vertical rules.**

#### Add footnote in table with `tablefootnote`





### Use `tabularx` package

```latex
\usepackage{tabularx}
```


>[!example]
> ```latex
> \begin{table}[tb]
> \centering
> \begin{tabular}{0.91\textwidth}{|m{107pt}<{\centering}|m{50pt}<{\centering}|m{50pt}<{\centering}|m{60pt}<{\centering}|m{60pt}<{\centering}|m{60pt}<{\centering}|}
> \hline 
> \multicolumn{6}{|c|}{Classification Accuracy ($\%$) mean $\pm$ standard error} \\ 
> \hline
> Dataset.& \multicolumn{2}{c|}{ MED (single views) } & SVM-2K  &  MV-MED    & CMV-MED \\ 
> \hline 
> \textbf{ARL Footstep} (Sensor 1,2, $|L|=50$) & $71.1\pm 5.3$ & $62.3 \pm 10.2$  & $73.3 \pm 5.2$ & $75.6 \pm 6.5$  & $\mathbf{85.5} \pm 6.1$ \\ 
> \hline 
> \textbf{WebKB4} ($|L|=15 $)&  $76.6 \pm 10.2$  & $77.1 \pm 10.1 $ & $79.0 \pm 10.0$ & $77.9 \pm 8.7 $  & $\mathbf{91.7} \pm 5.8$ \\ 
> \hline 
> \textbf{Internet Ads} ($|L|= 50$)& $87.3 \pm 0.9$ & $86.2 \pm 1.4$  & $82.5 \pm 4.3$ &  $88.8 \pm 2.3$ & $\mathbf{92.7} \pm 0.7 $\\ 
> \hline 
> \end{tabular} 
> \caption{Table name} 
> \label{tab: tab1}
> \end{table}
> ```

- `\begin{tabularx}{⟨width ⟩}[⟨pos ⟩]{⟨preamble ⟩} `
- `\hline`

-----------
##  Recommended Notes

- [CTAN - Comprehensive TEX Archive Network](https://www.ctan.org/)
	- package `booktabs` [reference](https://www.ctan.org/pkg/booktabs)
	- package `tabularx` [reference](https://www.ctan.org/pkg/tabularx)
	- package `tablefootnote` [reference](https://www.ctan.org/pkg/tablefootnote)

- Stack Overflow:
	- [Footnotes for tables in LaTeX](https://stackoverflow.com/questions/2888817/footnotes-for-tables-in-latex)

- Stack Exchange
	- [Table is too wide to fit in one page](https://tex.stackexchange.com/questions/172613/table-is-too-wide-to-fit-in-one-page)