---
tags:
  - concept
  - algorithm/analysis
keywords:
  - worst_case_running_time_analysis
topics:
  - algorithm/analysis
name: Algorithm Worst-Case Running Time Analysis
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Algorithm Worst-Case Running Time Analysis

![[Algorithm RAM Model and Running-Time Complexity Analysis#^76c416]]

>[!important] Definition
>The **worst-case (running-time) complexity** is the *longest running time* for *any input* of size $n$
>- The worst-case running time of an algorithm gives an *upper bound* on the running time for any input.
>- If you know it, then you have a *guarantee* that the algorithm *never takes any longer*.
>- We use *$O$-notation* for worst-case running time.

- [[Algorithm RAM Model and Running-Time Complexity Analysis]]
- [[Algorithm Big-O Notations and Dominance Relation]]


## Explanation

>[!quote] 
>The worst-case complexity generally proves to be **most useful** of these three measures in practice.
>
>-- [[Algorithm Design Manual by Skiena]] pp 33


>[!quote]
>For some algorithms, the worst case occurs fairly *often*. 
>- For example, in searching a database for a particular piece of information, the searching algorithm’s worst case often occurs when the information is *not present* in the database. 
>- In some applications, searches for absent information may be frequent.
>
>-- [[Introduction to Algorithms by Cormen]] pp  31




-----------
##  Recommended Notes and References

- [[Loop Invariant Format]]
- [[Algorithm General Definition]]

- [[Introduction to Algorithms by Cormen]] pp  31
- [[Algorithm Design Manual by Skiena]] pp 32