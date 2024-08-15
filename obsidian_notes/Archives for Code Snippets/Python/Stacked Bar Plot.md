---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-04-08
---

## Code Snippet Summary

>[!important]
>Plot two bar graphs, one stacked on top of the other


## Code


```python
import matplotlib.pyplot as plt

def plot_stack_bars_general(df, vars, id, time, custom_index,  xticks_rotations=0, savefig=True):
    fig, ax1 = plt.subplots(figsize=(20, 10))
    
    var1, var2 = vars
    plt.title('Counts of %s and %s for rule id %d ' % (var1, var2, id), fontsize=18)
    
    width = 0.6
    ticks = np.arange(0, df.shape[0], 1.0)*1.2
    rects1 = ax1.bar(ticks, df[var1], width, color='r',  label="firing counts for var1")
    rects2 = ax1.bar(ticks, df[var2], width, bottom=df[var1], color='b',  label="firing counts for var2")
    
    ax1.set_xlabel("index", fontsize=18)
    ax1.set_ylabel("counts", fontsize=18)
    ax1.tick_params('y', colors='b')
    ax1.tick_params(labelsize=18)
    
    plt.xticks(ticks, rotation=xticks_rotations, ha='center')
    if custom_index is None:
        ax1.set_xticklabels(df.index)
    elif len(custom_index) == len(ticks):
        ax1.set_xticklabels(custom_index)
         
    
    ax1.legend((rects1[0], rects2[0]), ('pass', 'cancel'), fontsize=18, loc=1)
    
    if savefig:
        filename = ("rule_" + str(id) + "_" + "_".join(vars) + "_"  + time + ".png")
        print("save fig to %s", (filename))
        plt.savefig(filename, bbox_inches='tight')
```



-----------
##  Recommended Notes


- [[Change Color of a single Bar]]