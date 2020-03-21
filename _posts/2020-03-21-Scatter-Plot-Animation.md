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
armsProbabilities = [0.1, 0.3, 0.45, 0.15]
mab1 = MAB(armsProbabilities)
```


```python
N_draws = 20
numOfArms = len(armsProbabilities)
# Each arm clolor
armColors = ['red','blue','orange','gray']

selectedArm = list()
rewardFromArm = list()
colorOfArm = list()
facecolorArm = list()
getFacecolor = lambda theArm,theReward: 'none' if theReward==0 else armColors[theArm]
for m in range(N_draws):
    # Choose the arm
    theArm = choice(range(numOfArms))
    # Get reward and regret from a given arm
    theReward, theRegret = mab1.draw(theArm) 
    # Record what have just happend
    selectedArm.extend([theArm])
    rewardFromArm.extend([theReward])
    colorOfArm.extend([armColors[theArm]])
    facecolorArm.extend([getFacecolor(theArm,theReward)])

print([ (armVal, rewardVal) for armVal, rewardVal in zip(selectedArm, rewardFromArm)])

```

    [(0, 0), (0, 0), (2, 1), (3, 0), (3, 0), (2, 1), (2, 0), (0, 1), (2, 1), (0, 0), (2, 1), (2, 0), (2, 0), (1, 1), (0, 0), (1, 0), (0, 0), (0, 0), (2, 0), (2, 0)]



```python
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
anim.save('a3.mp4', writer=writer)

Video('a3.mp4')
```




<video src="a3.mp4" controls  >
      Your browser does not support the <code>video</code> element.
    </video>




![png](output_3_1.png)



```python

```
