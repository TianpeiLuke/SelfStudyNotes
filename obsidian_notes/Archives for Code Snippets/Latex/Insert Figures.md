---
tags:
  - code
  - code_snippet
  - latex/figures
keywords: 
topics: 
language: latex
date of note: 2024-04-07
---

## Code Snippet Summary

>[!important]
>This is common sections that insert an image in latex 


## Code


```latex

\begin{figure}
\begin{minipage}[htb]{1\linewidth}
  \centering
  \centerline{\includegraphics[scale = 0.45]{figure1.png}}
\end{minipage}
\caption{\footnotesize{\textbf{Figure Name}}}
\label{fig: figure1}
\end{figure}

```

- `\begin{figure}[position] ... \end{figure}`
	- `position`: 
		- `h`
		- `t`
		- `b`
  
- `\begin{minipage}[position]{width} ... \end{minipage}`
	- `width`:

- `\includegraphics[control_parameter]{image_filepath}`:
	- `control_parameter`:
		- **`scale`**:

- `\caption{caption_text}`: 
- `\label{fig: figure_label}`: 

### Trim and Clip Image

```latex
\begin{figure}[htb] 
\begin{minipage}[b]{1\linewidth}
  \centering
  \centerline{\includegraphics[trim = 10mm 65mm 32mm 60mm, clip, scale = 0.28]{figure2.eps}}
\end{minipage}
\caption{\footnotesize{Figure 2.}}
\label{fig: figure2}
\end{figure}
```

- `\includegraphics[control_parameter]{image_filepath}`:
	- `control_parameter`:
		- **`trim`**:
		- **`clip`**: 


### Multiple Plots share one Figure

```latex
\begin{figure*}[tb] 
\begin{minipage}[b]{0.28\linewidth}
  \centering
  \centerline{\includegraphics[...]{image1.eps}}
  \vspace{-7pt}
  \centerline{\footnotesize{(a)}}
\end{minipage}

\hfill

\begin{minipage}[b]{0.28\linewidth}
  \centering
  \centerline{\includegraphics[...]{image2.eps}}
  \vspace{-7pt}
 \centerline{\footnotesize{(b) }}
\end{minipage}

\hfill

\begin{minipage}[b]{0.3\linewidth}
  \centering
  \centerline{\includegraphics[...]{image3.eps}}
  \vspace{-7pt}
 \centerline{\footnotesize{(c) }}
\end{minipage}

\caption{Figure name. (a) Description Sub-Figure (a). (b) Description Sub-Figure (b). (c) Description Sub-Figure (c).}}
\label{fig: figure3}
\end{figure*}
```




-----------
##  Recommended Notes

