---
title: "Scatter plot animation in Python"
date: 2020-03-21
categories: [Snippet]
tags: [Python, plot]
excerpt: "A simple Python code pattern of how to produce mp4 animation of scatter plot"
mathjax: "true"

---

```python
from arm import MAB
import numpy as np 
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation
import matplotlib.animation as animation
from IPython.display import Video
from random import choice
```


```python
# Create some data for scatter plot:
# - index in the array (from 0...) is the x axis
# - selectedArm is the y axis value from the list [0,1,2,3]
# - rewardFromArm is the value either 0 or 1 and controls if plotted dot is empty inside
# - colorOfArm gives different colors of each y axis value
# - facecolorArm controls color of the dot is it is not empty (see rewardFromArm) 
```


```python
N_draws = 20
numOfArms = 4 
selectedArm   = [3, 0, 2, 2, 2, 1, 2, 1, 0, 0, 2, 1, 0, 1, 0, 3, 3, 1, 1, 2]
rewardFromArm = [1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 0, 0, 1, 1, 0]
colorOfArm    = ['gray', 'red', 'orange', 'orange', 'orange', 'blue', 'orange',\
                 'blue', 'red', 'red', 'orange', 'blue', 'red', 'blue', 'red', \
                 'gray', 'gray', 'blue', 'blue', 'orange']
facecolorArm  = ['gray', 'none', 'none', 'none', 'none', 'none', 'none', 'none',\
                 'red', 'none', 'none', 'blue', 'none', 'none', 'none', 'none', \
                 'none', 'blue', 'blue', 'none']
```


```python
defaultPlot = False
if defaultPlot:
    plt.rcParams['axes.facecolor'] = plt.rcParamsDefault['axes.facecolor']
    plt.rcParams['axes.edgecolor'] = plt.rcParamsDefault['axes.edgecolor']
    plt.rcParams['axes.grid'] = plt.rcParamsDefault['axes.grid']
    plt.rcParams['grid.alpha'] = plt.rcParamsDefault['grid.alpha']
    plt.rcParams['grid.color'] = plt.rcParamsDefault['grid.color']
else:
    plt.rcParams['axes.facecolor'] = '#D9D9D9'
    plt.rcParams['axes.edgecolor'] = 'gray'
    plt.rcParams['axes.grid'] = True
    plt.rcParams['grid.alpha'] = 0.35
    #plt.rcParams['grid.color'] = "#D9D9D9"
    
f = plt.figure(figsize=(10,5))
f.subplots_adjust(top=0.8, wspace=0.025)
f.tight_layout()
ax1 = plt.subplot(111, xlim=(-0.5, N_draws), ylim=(-0.5, numOfArms - 0.5), 
                  yticks=[ yVal for yVal in range(numOfArms)], yticklabels=[ yVal for yVal in range(numOfArms)],
                  xticks=[0.0,5.0,10.0,15.0,20.0], xticklabels={0,5,10,15,20})

scat = ax1.scatter(x=[list(range(N_draws))[0]], y=[selectedArm[0]], c=[colorOfArm[0]], s=70,\
                   marker='o', facecolor=[facecolorArm[0]])

# Animation update function
def animationUpdate(k):
    x = list(range(N_draws))[:k]
    y = selectedArm[:k]
    scat.set_offsets(np.c_[x,y])
    scat.set_color(colorOfArm[:k])
    scat.set_facecolor(facecolorArm[:k])
    return scat,

# function for creating animation
anim = FuncAnimation(f, animationUpdate, frames=N_draws, interval=400, blit=True)

# Set up formatting for the movie files
Writer = animation.writers['ffmpeg']
writer = Writer(fps=3, bitrate=1800)
anim.save('scatterPlotAnimation_v1.mp4', writer=writer)

Video('scatterPlotAnimation_v1.mp4')
```

![video](/images/scatterPlotAnimation_v1.mp4)


<video src="scatterPlotAnimation_v1.mp4" controls  >
      Your browser does not support the <code>video</code> element.
    </video>


Other interesting plots (joint scatter and histogram combined)
https://seaborn.pydata.org/generated/seaborn.JointGrid.html
