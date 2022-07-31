+++
author = "happysxpp"
title = "Understanding the View Frustum"
date = "2022-07-31"
description = "The word frustum refers to a solid shape that looks like a pyramid with the top cut off parallel to the base."
tags = [
    "frustum",
    "view frustm",
]

+++

<!--more-->

# Understanding the View Frustum

The word **frustum** refers to a solid shape that looks like a pyramid with the top cut off parallel to the base. This is the shape of the region that can be seen and rendered by a perspective **camera**. The following thought experiment should help to explain why this is the case.

The rod could just as easily be moved and rotated left, right, or down or any combination of horizontal and vertical. The angle of the “hidden” rod simply depends on its distance from the centre of the screen in both axes.

The meaning of this thought experiment is that any point in a camera’s image actually corresponds to a line in world space and only a single point along that line is visible in the image. Everything behind that position on the line is obscured.

The outer edges of the image are defined by the diverging lines that correspond to the corners of the image. If those lines were traced backwards towards the camera, they would all eventually converge at a single point. In Unity, this point is located exactly at the camera’s transform position and is known as the centre of perspective. The angle subtended by the lines converging from the top and bottom centres of the screen at the centre of perspective is called the field of view (often abbreviated to FOV).

As stated above, anything that falls outside the diverging lines at the edges of the image will not be visible to the camera, but there are also two other restrictions on what it will render. The near and far clipping planes are parallel to the camera’s XY plane and each set at a certain distance along its centre line. Anything closer to the camera than the near **clipping plane**and anything farther away than the **far clipping plane**  will not be rendered.

The diverging corner lines of the image along with the two clipping planes define a truncated pyramid - the view frustum.
