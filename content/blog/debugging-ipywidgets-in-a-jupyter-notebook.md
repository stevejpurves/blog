---
title: Debugging ipywidgets in a Jupyter Notebook
description: A quick tip for easier debugging with ipywidgets in Jupyter Notebooks
date: '2022-12-02T11:05:59.800Z'
name: debugging-ipywidgets-in-a-jupyter-notebook
oxa: oxa:DOHMeg040aVXqR51yjBy/FjveA2PQluCWbJNuXPVh
subtitle: Stop your error messages from being eaten
short_title: ''
tags:
  - ipywidgets
  - jupyter
  - python
thumbnail: thumbnails/debugging-ipywidgets-in-a-jupyter-notebook.png
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/wbYuoSh8lO3xobQnapiu.3","tags":[]}

The `ipywidgets` library offers a big collection of standard widgets and supports some really powerful third-party widgets to like `ipympl`, `ipyleaflet` and more... So you can build some pretty sophisticated UI right in your Jupyter Notebook, then launch your app as a dashboard with `voila` or (ok, very soon!) create an interactive document with [Curvenote](https://curvenote.com).

When your UI starts getting bigger, developing and debugging can be tricky though — for numerous reasons — but the biggest thing is often lack of access to `stdout` and `stderr` from the various callback functions that you end up creating. Luckily there is a simple trick that helps solve this.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/kBvYNqToE8zqisYlQndj.2","tags":[]}

## A broken example

The following code has a problem, it will happily render my `ipympl` plot 👏 but the pick event does not work. When I pick on the plot nothing happens at all, no feedback, no error message, nada.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/pNUSQlsb20mjsQ4pInn8.3","tags":[]}

```python
import matplotlib.pyplot as plt
import numpy as np

%matplotlib widget

plt.ioff()
fig, ax = plt.subplots(1, 1, figsize=(4,4))
plt.ion()

ax.plot(np.sin(np.random.random(100)),picker=True, pickradius=2)

selection = { "line": None }

def onpick(e):
    m = e.mouseevent
    e.artist.set__color('#DC143C')    
    e.artist.set_zorder(10)
    e.artist.set_linestyle('-')
    e.artist.set_marker('o')
    e.artist.set_markersize(e.artist.get_markersize() + 1)
    selection["line"] = e.artist
    

cid = fig.canvas.mpl_connect('pick_event', onpick)

display(fig.canvas)
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/9Pc1gHqahbTh5gW6kcFh.2","tags":[]}

```{figure} images/DOHMeg040aVXqR51yjBy-AzwMYrH2WdsNU5AqijkT-v1.gif
:name: gilDb8Ttsw
:align: center
:width: 60%
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/cXCcoHAJqL9VRaZOAz3h.2","tags":[]}

The problem is actually on the line 👇
```
    e.artist.set__color('#DC143C')
```

Where there should be only one underscore, but the `stderr` generated in the callback function gets eaten. To solve this we need to set up a way for `stderr` to get out to the notebook interface. We can do this with `ipywidgets`, specifically the `Output` widget!

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/HxQoX4noQhhg6hQjlZsD.4","tags":[]}

## Debugging with an output widget

We need to do 3 things:

- Create an instance of an `Output` widget at the top of our code
- `display(...)` our debug `Output` widget somewhere (doesn't have to be in the same cell)
- We add a conditional `with context` block at the top of our event handlers

After that, we get error messages showing up on our output display, and can also `print(...)` temporary debug messages there too while developing. To remove the output, we can remove the code that creates the instance and the conditional context blocks can stay in our callbacks.

And 💥 we now have `stderr` output!

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/ZjAs3gkd1sWymPchmC2D.3","tags":[]}

```python
%matplotlib widget

# create an output widget!
w_debug_output = Output()

plt.ioff()

fig, ax = plt.subplots(1, 1, figsize=(4,4))
plt.ion()
ax.plot(np.sin(np.random.random(100)),picker=True, pickradius=2)

def onpick(e):
    with w_debug_output if w_debug_output else nullcontext():
        m = e.mouseevent
        e.artist.set__color('#DC143C')    
        e.artist.set_zorder(10)
        e.artist.set_linestyle('-')
        e.artist.set_marker('o')
        e.artist.set_markersize(e.artist.get_markersize() + 1)
        selection["line"] = e.artist

cid = fig.canvas.mpl_connect('pick_event', onpick)

display(fig.canvas)
display(w_debug_output)
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/ndpUDsOapBC2u7zt9PiG.2","tags":[]}

```{figure} images/DOHMeg040aVXqR51yjBy-pnJpe04yDMVCRQ29Y6su-v1.gif
:name: ArelxFUKx3
:align: center
:width: 60%
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/MqAM7jkowUAcUnzST5Y0.3","tags":[]}

This makes it pretty easy to fix our error here and chance to catch other errors while developing with `ipywidgets` in a notebook. Also we can now `print` debug messages and they’ll also appear in the `Output` widget too.

Here's the result of this example code working below:

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/SuiYH0FrFBJN2Lz0p1yl.2","tags":[]}

```python
%matplotlib widget

# create an output widget!
w_debug_output = Output()

plt.ioff()

fig, ax = plt.subplots(1, 1, figsize=(4,4))
plt.ion()
ax.plot(np.sin(np.random.random(100)),picker=True, pickradius=2)

def onpick(e):
    with w_debug_output if w_debug_output else nullcontext():
        m = e.mouseevent
        e.artist.set_color('#DC143C')    
        e.artist.set_zorder(10)
        e.artist.set_linestyle('-')
        e.artist.set_marker('o')
        e.artist.set_markersize(e.artist.get_markersize() + 1)
        selection["line"] = e.artist

cid = fig.canvas.mpl_connect('pick_event', onpick)

display(fig.canvas)
display(w_debug_output)
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/dDfwBhLSq8g07hD7HE9J.2","tags":[]}

```{figure} images/DOHMeg040aVXqR51yjBy-sfTtnAUzUSytH3JCmrrD-v1.gif
:name: SuTef2sxDy
:align: center
:width: 60%
```

