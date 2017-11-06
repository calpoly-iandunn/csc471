---
layout: assignment
assignment: "lab09"
title: Lab 9
---

<div class="alert alert-dismissible alert-danger">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <h4>Warning!</h4>
  <p>
    This content is not fully ready yet.
    The details of the assignment may change, and base code is not yet available!
  </p>
</div>

## Texture mapping

Today we will play with texture mapping.

You are given code the draws three different shape each with its own unique texture: a ground plane, a dog and a sphere.
Note that the base code includes very fake lighting in the form of a directional light and diffuse shading only.
The starting view should look as follows:

{% include image-block.html file="lab9_1.png" alt="Lab 9 Figure 1" %}

The code has a very simplified UI that allows you to rotate the objects using `A` and `D` – a side view looks as follows:

{% include image-block.html file="lab9_2.png" alt="Lab 9 Figure 2" %}

You have three tasks that you must complete.
But start by looking at `init` in main.cpp to see how it is different and also look at the three different fragmenet shaders and the one shared vertex shader.
Make sure you understand the limitation of the shading implementation.

Now:

1. Find a better “fur” texture for the dog instead of the crate texture.
  Note the file must be a 24 bit bmp image

2. Now edit both texture.cpp and main.cpp to make the grass texture repeat over the plane.
  You will need to change the WRAP parameters for s and t and you will need to change the texture coordinates of the ground plane.
  Look at `initGeom` and look at the appropriate `glTexParameterf` call.

3. Now modify the fragment shader for the world.
  Do something creative per pixel – for example, stop drawing the fragments associated with the ocean or add a specular component to the ocean only.
  Be creative.
  The effect must be clearly discernable.

Example output showing all three changes:

{% include image-block.html file="lab9_3.png" alt="Lab 9 Figure 3" %}
