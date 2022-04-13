---
layout: post
title:  "Making pangolin work with Python"
date:   2022-04-13 23:52:15 +0200
categories: python
---
You may have run into errors trying to use the [pangolin](https://github.com/uoip/pangolin) library for Python by uoip. His fork hasn't been updated in a while. Here is how to use pangolin the the correct way.

In 2022, pangolin - [stevenlovegrove's repo](https://github.com/stevenlovegrove/Pangolin) actually has python bindings - so you don't need to use uoip's fork.

You can read the README [here](https://github.com/stevenlovegrove/Pangolin) for installing it (install from the master branch), but the main thing to note are the out of date code samples.

pangolin.View.SetBounds now takes in different arguments. If you try to call it with float values, it complains that it doesn't match a function. I've modified [markoelez's](https://github.com/markoelez/Pangolin/blob/master/python/examples/HelloPangolin.py) code to work.

```python
import OpenGL.GL as gl
import pypangolin as pangolin
import numpy as np

def main():
    pangolin.CreateWindowAndBind('Main', 640, 480)
    gl.glEnable(gl.GL_DEPTH_TEST)

    # Define Projection and initial ModelView matrix
    scam = pangolin.OpenGlRenderState(
        pangolin.ProjectionMatrix(640, 480, 420, 420, 320, 240, 0.2, 100),
        pangolin.ModelViewLookAt(-2, 2, -2, 0, 0, 0, pangolin.AxisDirection.AxisY))
    handler = pangolin.Handler3D(scam)

    # this was out of date.
	dcam = (
        pn.CreateDisplay()
        .SetBounds(
            pn.Attach(0),
            pn.Attach(1),
            pn.Attach.Pix(180),
            pn.Attach(1),
            -640/480,
            )
        .SetHandler(handler)
	)

    while not pangolin.ShouldQuit():
        gl.glClear(gl.GL_COLOR_BUFFER_BIT | gl.GL_DEPTH_BUFFER_BIT)
        gl.glClearColor(1.0, 1.0, 1.0, 1.0)
        dcam.Activate(scam)
        
        # Render OpenGL Cube
        pangolin.glDrawColouredCube()

        # Draw Point Cloud
        points = np.random.random((100000, 3)) * 10
        colors = np.zeros((len(points), 3))
        colors[:, 1] = 1 -points[:, 0] / 10.
        colors[:, 2] = 1 - points[:, 1] / 10.
        colors[:, 0] = 1 - points[:, 2] / 10.

        gl.glPointSize(2)
        gl.glColor3f(1.0, 0.0, 0.0)
        # access numpy array directly(without copying data), array should be contiguous.
        pangolin.DrawPoints(points, colors)    

        pangolin.FinishFrame()



if __name__ == '__main__':
    main()
```

I hope this helped you. Feel free to check out the other things I make. Or join my [Discord](my://discord.com/invite/UkMNCJu2x3)

