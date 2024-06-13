---
tags:
  - code
  - code_snippet
  - latex/algorithm_descrp
keywords: 
topics: 
language: latex
date of note: 2024-04-08
---

## Code Snippet Summary

>[!important]
>- Create Algorithm description in Latex
>- Use `algorithm` package


## Code

```latex
\usepackage{algorithm}
\usepackage{algpseudocode}
\usepackage{algcompatible}
```


```latex
\begin{algorithm}[t]
  \caption{GEM regularized MED }
  \label{alg: g-med}
  \begin{algorithmic}[1]
  %\algsetup{fontsize=\footnotesize}%
  \small{ 
  \REQUIRE $ \mathcal{D} \equiv \{  (\mathbf{x}_{n}, \, \mathbf{y}_{n} )\}_{n=1}^{N}$,  where $\footnotesize{\mathbf{x}_{n} \in \mathcal{R}^{p}}$, $\footnotesize{\mathbf{y}_{n} \in \{\pm1\} }$. Prior distribution $p_{0}(\Theta)$, $p_{0}(\eta_{n})$ and the upper bound $S_{c},c\in\{\pm1\}$.  \vspace{-10pt}

  \STATE \textbf{Initialize:} Set $\boldsymbol{\mu}_{0} = \mathbf{0}$. $\boldsymbol{\alpha}_{0}$ is set by applying  MED on $\mathcal{D} $ \vspace{-1pt}
  
  \FOR{$t=1,\ldots, T$ or until converge}%\vspace{1pt}
    \STATE  Compute the gradient of log-partition function w.r.t\; $\boldsymbol{\alpha}_{t}$ and $\boldsymbol{\mu}_{t}$,  respectively, as
    \begin{footnotesize}
    \setlength{\abovedisplayskip}{1pt}
    \setlength{\belowdisplayskip}{1pt}
     \begin{eqnarray*}
	 \frac{\partial \log Z(\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t})}{\partial \alpha_{n}}
	\hspace{-10pt}&=&\hspace{-5pt}  \mathds{E}_{p(\Theta, \boldsymbol{\eta}|\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t}, \mathcal{D})}	\left[\eta_{n}\left\{ \Delta F(y_{n}, \mathbf{x}_{n}; \Theta)  -1 \right\} \right], \\
 	\hspace{-10pt}&&\hspace{-10pt}\qquad n=1,\ldots,N,\\%\label{eqn: grad_logZ_alpha}\\[10pt]
 \frac{\partial \log Z(\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t})}{\partial \mu_{c}}
\hspace{-10pt}&=&\hspace{-5pt} \mathds{E}_{p(\Theta, \boldsymbol{\eta}|\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t}, \mathcal{D})}\left[\sum_{n: y_{n} = c}\eta_{n}\frac{\log(\hat{p}(\mathbf{x}_{n}))}{N} +S_{c} \right]\\%\qquad\label{eqn: grad_logZ_mu}
&& \qquad c \in \{-1,+1\},
\end{eqnarray*}
\end{footnotesize} 
where the expectation is approximated via Gibbs sampling with the conditional density $\footnotesize {p(\boldsymbol{\eta}|\hat{\Theta},  \mathcal{D}) = \prod_{n=1}^{N}p(\eta_{n}|\hat{\Theta},  \mathcal{D})}$ and $\footnotesize{p(\Theta|\hat{\boldsymbol{\eta}},  \mathcal{D})}$ computed explicitly. \vspace{5pt}
  \STATE Update $\alpha_{n}$ and $\mu_{c}$ via projected gradient descent, i.e. 
     \begin{footnotesize}
      \setlength{\abovedisplayskip}{1pt}
      \setlength{\belowdisplayskip}{1pt}
    \begin{eqnarray*}
\alpha_{n,(t+1)} &=& \text{proj}_{\{\alpha:\, 0\le \alpha \le 1 \}}\left\{\alpha_{n,t} - \varphi\,\frac{\partial \log Z(\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t})}{\partial \alpha_{n}} \right\}\nonumber\\
&&n=1,\ldots,N,\\
 \mu_{c,(t+1)} &=& \text{proj}_{\{\mu:\, 0\le \mu \le C \}}\left\{\mu_{c,t} - \psi\,\frac{\partial \log Z(\boldsymbol{\alpha}_{t},\boldsymbol{\mu}_{t})}{\partial \mu_{c}}\right\} \nonumber\\
&&c\in\{-1, +1\}, \vspace{-5pt}
     \end{eqnarray*}
\end{footnotesize}\hspace{-5pt}
where $\text{proj}_{\{w:\, 0\le w \le C \}}\{w\}\equiv \min\left(\max(w, 0),C\right)$ defines the projection of $w$ on the feasible set $\{w:\, 0\le w\le C \}$  via clipping and $\psi,\,\varphi>0$ define the learning rate.
\ENDFOR  %
\vspace{2pt}
\ENSURE Assign label for test sample $\mathbf{x}$ as 
 \begin{scriptsize}
\setlength{\abovedisplayskip}{1pt}
\setlength{\belowdisplayskip}{0.5pt} 
\begin{equation*}
\hat{y} = \argmax_{y} \int\,p(y | \mathbf{x}, \; \Theta)\,p(\Theta |\mathcal{D})d \Theta, %\vspace{-10pt}
\end{equation*} 
\end{scriptsize}\hspace{-7pt}
where $\scriptsize{p(\Theta |\mathcal{D})= \sum_{\boldsymbol{\eta} \in \{0,1\}^{N}}p(\Theta, \boldsymbol{\eta} \,|\,\mathcal{D})}$ \hspace{-2pt} is computed via marginalization. \hspace{-5pt} Also obtain the posterior on $\boldsymbol{\eta}$ at the final iteration of step 4, $ \scriptsize{\{\pi_{n}\equiv p(\eta_{n,T}=1 |  \Theta_{T}, \mathcal{D})\}}$, as the anomaly scores. 
 }
 \end{algorithmic} 
\end{algorithm}  
```

- `\begin{algorithm}[position] ... \end{algorithm}`

- `\begin{algorithmic}[width] ... \end{algorithmic}`
	- `\REQUIRE`
	- `\STATE`
	- `\FOR{...} ... \ENDFOR`



-----------
##  Recommended Notes

