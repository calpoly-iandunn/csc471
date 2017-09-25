---
layout: page
active: lectures
title: "Lecture 0: Introduction"
auto-title: true
---

**Motivation:** Draw shapes/geometry to 2D screen.

- Spaces
  - Where do we store geometry of scene?
    - "World" coordinates
  - Mesh data structure
    - Indexed-face set
  - What is a picture?
    - pixels

To draw something, we need to transform from world to pixel!

- Before transform, we must constrain the view into the world
- This includes accounting for aspect ratio

$$ L = -w / h $$

$$ R = w / h $$

$$ B = -1 $$

$$ T = 1 $$

In general, transforms can look like this:

$$ x_p = c * x_w + d $$

$$ y_p = e * y_w + f $$

Where $$ c $$ and $$ e $$ are scales and $$ d $$ and $$ f $$ are shifts.


## Overview of P1

1. Read in triangles
2. Convert to window coordinates
3. Bound and test with barycentric coordinates

