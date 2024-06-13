---
tags:
  - code
  - code_snippet
  - latex/symbols
keywords: 
topics: 
language: latex
date of note: 2024-04-07
---

## Code Snippet Summary

>[!important] 
>This is a style file `Tianpei_Report.sty` that simplifies some commonly used symbols


## Code

### Letters

```latex
\newcommand{\defeq}{\vcentcolon=}
\newcommand{\eqdef}{=\vcentcolon}

// Different Fonts 
\newcommand{\cA}{{\mathcal A}}
\newcommand{\cB}{{\mathcal B}}
\newcommand{\cC}{{\mathcal C}}
\newcommand{\cD}{{\mathcal D}}
\newcommand{\cE}{{\mathcal E}}
\newcommand{\cF}{{\mathcal F}}
\newcommand{\cG}{{\mathcal G}}
\newcommand{\cH}{{\mathcal H}} 
\newcommand{\cI}{{\mathcal I}} 
\newcommand{\cL}{{\mathcal L}}
\newcommand{\cK}{{\mathcal K}}
\newcommand{\cM}{{\mathcal M}}
\newcommand{\cN}{{\mathcal N}}
\newcommand{\cO}{{\mathcal O}}
\newcommand{\cP}{{\mathcal P}}
\newcommand{\cQ}{{\mathcal Q}}
\newcommand{\cR}{{\mathcal R}}
\newcommand{\cS}{{\mathcal S}}
\newcommand{\cT}{{\mathcal T}}
\newcommand{\cW}{{\mathcal W}}
\newcommand{\cU}{{\mathcal U}}
\newcommand{\cV}{{\mathcal V}}
\newcommand{\cX}{{\mathcal X}} 
\newcommand{\cY}{{\mathcal Y}} 
\newcommand{\cZ}{{\mathcal Z}} 

\newcommand{\bA}{{\mathbb A}}
\newcommand{\bB}{{\mathbb B}}
\newcommand{\bC}{{\mathbb C}}
\newcommand{\bG}{{\mathbb G}}
\newcommand{\bH}{{\mathbb H}}
\newcommand{\bL}{{\mathbb L}}
\newcommand{\bM}{{\mathbb M}}
\newcommand{\bN}{{\mathbb N}}
\newcommand{\bP}{{\mathbb P}}
\newcommand{\bQ}{{\mathbb Q}}
\newcommand{\bR}{{\mathbb R}}
\newcommand{\bS}{{\mathbb S}}
\newcommand{\bT}{{\mathbb T}}
\newcommand{\bV}{{\mathbb V}}
\newcommand{\bZ}{{\mathbb Z}}

\newcommand{\srA}{{\mathscr A}}
\newcommand{\srB}{{\mathscr B}}
\newcommand{\srC}{{\mathscr C}}
\newcommand{\srD}{{\mathscr D}}
\newcommand{\srE}{{\mathscr E}}
\newcommand{\srF}{{\mathscr F}}
\newcommand{\srG}{{\mathscr G}}
\newcommand{\srH}{{\mathscr H}}
\newcommand{\srI}{{\mathscr I}}
\newcommand{\srJ}{{\mathscr J}}
\newcommand{\srK}{{\mathscr K}}
\newcommand{\srL}{{\mathscr L}}
\newcommand{\srM}{{\mathscr M}}
\newcommand{\srN}{{\mathscr N}}
\newcommand{\srO}{{\mathscr O}}
\newcommand{\srP}{{\mathscr P}}
\newcommand{\srQ}{{\mathscr Q}}
\newcommand{\srR}{{\mathscr R}}
\newcommand{\srS}{{\mathscr S}}
\newcommand{\srT}{{\mathscr T}}

\newcommand{\frA}{{\mathfrak A}}
\newcommand{\frG}{{\mathfrak G}}
\newcommand{\frM}{{\mathfrak M}}
\newcommand{\frP}{{\mathfrak P}}
\newcommand{\frR}{{\mathfrak R}}
\newcommand{\frS}{{\mathfrak S}}
\newcommand{\frX}{{\mathfrak X}}

\newcommand{\sR}{{\mathds R}}

\newcommand{\pzcP}{{\mathpzc P}}
```

### Operators

```latex
\newcommand\indep{\protect\mathpalette{\protect\independenT}{\perp}} %% statistical independence

\newcommand{\floor}[1]{\left\lfloor #1 \right\rfloor} % floor
\newcommand{\ceil}[1]{\left\lceil #1 \right\rceil}    % ceil

\newcommand{\mb}[1]{\boldsymbol{#1}}                  % math bold
\newcommand{\sech}{\mathrm{sech}\,}
\newcommand{\tr}[1]{\mathrm{tr}\left(#1 \right) }
\newcommand{\ind}[1]{\mathds{1}\left\{ #1 \right\}}   % indicator function
\newcommand{\brac}[1]{\left[#1\right]}                % [x]
\newcommand{\set}[1]{\left\{#1\right\}}               % {x}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}     % |x|
\newcommand{\paren}[1]{\left(#1\right)}               % (x)
\newcommand{\norm}[2]{\left\|#1\right\|_{#2}}         % ||x||
\newcommand{\kl}[2]{\mathds{KL}\left( #1 \left\|\right. #2 \right)} % KL divergence
\newcommand{\divg}[3]{\mathds{D}^{#1}\left( #2 \left\|\right. #3 \right)} % divergence
\newcommand{\E}[2]{\mathds{E}_{#1}\left[ #2 \right]}            % expectation
\newcommand{\Em}[2]{\widehat{\mathds{E}}_{#1}\left[ #2 \right]} % empirical expectation
\newcommand{\diag}[1]{\text{diag}\left(#1\right)}               % diagonalize
\newcommand{\vect}[1]{\text{vec}\left(#1\right)}                % vectorize
\newcommand{\inn}[2]{\left\langle  #1\,,\, #2   \right\rangle}  % inner product
\newcommand{\cov}[2]{\text{cov}\left(  #1\,,\, #2   \right)}    % covariance
\newcommand{\partdiff}[2]{\frac{\partial #1}{ \partial #2}}     % partial differential
\newcommand{\dpartdiff}[2]{\dfrac{\partial #1}{ \partial #2}}   % partial differential
\newcommand{\grad}[1]{\nabla_{#1}}                              % gradient
\newcommand{\conn}[2]{\nabla_{#1}{#2}}                          % connections
\newcommand{\tanconn}[2]{\nabla^{\top}_{#1}{#2}}                % tangential connections
\newcommand{\orthconn}[2]{\nabla^{\perp}_{#1}{#2}}              % orthogonal connections
\newcommand{\sign}[1]{\text{sign}\left\{#1\right\}}             % sign function
\newcommand{\sgn}[1]{\text{sgn}\left(#1\right)}                 % sign function
\newcommand{\iprod}[1]{\mathbin{\lrcorner }{#1}}                % 
\newcommand{\xdotx}[1]{\,{#1}\ldots{#1}\,}                      % a ... a
%\newcommand{\indep}{\perp \!\!\! \perp}
```
### Environments

```latex
\newtheorem{theorem}{\textbf{Theorem}}[section]
\newtheorem{lemma}[theorem]{\textbf{Lemma}}
\newtheorem{result}[theorem]{\textbf{Result}}
\newtheorem{assumption}[theorem]{\textbf{Assumption}}
\newtheorem{principle}[theorem]{\textbf{Principle}}
\newtheorem{proposition}[theorem]{\textbf{Proposition}}
\newtheorem{corollary}[theorem]{\textbf{Corollary}}
\newtheorem{exercise}[theorem]{\textbf{Exercise}}

\newenvironment{solution}[1][Solution:]{\begin{trivlist}
\item[\hskip \labelsep {\bfseries #1}]}{\end{trivlist}}
\newenvironment{proof}[1][Proof:]{\begin{trivlist}
\item[\hskip \labelsep {\bfseries #1}]}{\end{trivlist}}
\newenvironment{definition}[1][Definition]{\begin{trivlist}
\item[\hskip \labelsep {\bfseries #1}]}{\end{trivlist}}
\newenvironment{example}[1][Example]{\begin{trivlist}
\item[\hskip \labelsep {\bfseries #1}]}{\end{trivlist}}
\newenvironment{remark}[1][Remark]{\begin{trivlist}
\item[\hskip \labelsep {\bfseries #1}]}{\end{trivlist}}
```

### Special Symbols

```latex
\newcommand{\qed}{\nobreak \ifvmode \relax \else
      \ifdim\lastskip<1.5em \hskip-\lastskip
      \hskip1.5em plus0em minus0.5em \fi \nobreak
      \vrule height0.75em width0.5em depth0.25em\fi}    % QED []
      
\newcommand*{\QEDA}{\hfill\ensuremath{\blacksquare}}%   % QED []
\newcommand*{\QEDB}{\hfill\ensuremath{\square}}         % QED []

```


-----------
##  Recommended Notes

