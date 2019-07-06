---
title: "Bar plots in Python"
date: 2019-07-05
tags: [Python, plot]
excerpt: "A simple Python code pattern of how to plot a bar plot"
mathjax: "true"

---

```python
import matplotlib.pyplot as plt
import numpy as np
```

```python
track1 = np.asarray([ 10, 20, 40, 80 ])
track2 = np.asarray([ 5, 25, 30, 70 ])
track3 = np.asarray([ 12, 18, 76, 92])

barWidth = 0.22
x1 = np.arange(len(track1))
x2 = [ x + barWidth for x in x1]
x3 = [ x + barWidth for x in x2]
```

```python
figSize = (10,5)
f = plt.figure( figsize=figSize)
f.subplots_adjust(top=0.8, wspace=0.025)
f.tight_layout()
ax1 = plt.subplot(111)
a = ax1.set_title('Tracks intensity in different scenarios')
ax1.bar( x1, track1, color='#7f6d5f', width=barWidth, edgecolor='white', label='track 1')
ax1.bar( x2, track2, color='#557f2d', width=barWidth, edgecolor='white', label='track 2')
ax1.bar( x3, track3, color='#2d7f5e', width=barWidth, edgecolor='white', label='track 3')
ax1.set_xlabel('Tracks in different scenarios',fontsize=15, color='gray')
ax1.set_ylabel('Track intensity [%]',fontsize=14, color='gray')
a=ax1.set_xticks(x2)
a=ax1.set_xticklabels({'scenario 1','scenario 2','scenario 3','scenario 4'})
a=ax1.grid()
a=ax1.legend()
plt.show()
```

![image](/images/bar_plot_side_by_side.png)


```python
barWidth = 0.6
x1 = np.arange(len(track1))
track12 = np.add(track1,track2).tolist()
```

```python
figSize = (10,5)
f = plt.figure( figsize=figSize)
f.subplots_adjust(top=0.8, wspace=0.025)
f.tight_layout()
ax1 = plt.subplot(111)
a = ax1.set_title('Tracks intensity in different scenarios')

p1 = ax1.bar(x1,track1, barWidth, color='#7f6d5f', edgecolor='white', label='track 1')
p2 = ax1.bar(x1, track2, barWidth, color='#557f2d', bottom=track1, edgecolor='white', label='track 2')
p2 = ax1.bar(x1, track3, barWidth, color='#2d7f5e', bottom=track12, edgecolor='white', label='track 3')

ax1.set_xlabel('Tracks in different scenarios',fontsize=15, color='gray')
ax1.set_ylabel('Track intensity [%]',fontsize=14, color='gray')
a=ax1.set_xticks(x1)
a=ax1.set_xticklabels({'scenario 1','scenario 2','scenario 3','scenario 4'})
#a=ax1.set_yscale("log")
a=ax1.legend()
plt.show()
```

![image](/images/bar_plot_one_on_top_of_another.png)
