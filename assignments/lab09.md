---
layout: assignment
assignment: "lab09"
title: Lab 9
---

## Texture Mapping and Multishape Models

Today we will play with texture mapping and refine the shape code in order to handle `obj` files that have more than one shape.

You are given code the draws three different shapes.
Two with their own unique texture: a ground plane and a sphere textured like the world.
Note that the base code includes very fake lighting in the form of a directional light and diffuse shading only.
The starting view should look as follows:

{% include image-block.html file="lab9_1.png" alt="Lab 9 Figure 1" %}

### Step 1: Modify the code to be able the load multi-shape obj files

In preparation for your final projects, many `obj` files on like are made up for more then one shape.
Fix the base code to be able to display a mesh from an `obj` file with multiple "shapes".
By default the older code we have worked with on displayed `shape[0]` from the obj file.
The new base code is set up so that you can create a “Shape” object for each of the tiny_obj "shapes".
You need to fix the code in "initGeom" in `main.cpp` and you need to compute the bounds of the entire mesh to make sure it can display at the origin and a reasonable scale.
Once you have this code in place, you should be able to load in ans see the whole `dummy.obj` model.
See the below figure for an example:

{% include image-block.html file="lab9_2.png" alt="Lab 9 Figure 2" %}

### Step 2: Play with texture mapping

You have three tasks that you must complete.
But start by looking at the code and have some idea of how textures are being controlled.
Make sure you understand the limitation of the shading implementation.

Now:

1. Add another sphere to the world and find a new texture to load in and texture the second sphere with that is different then the already loaded textures.

2. Now edit both `texture.cpp` and `main.cpp` to make the grass texture repeat over the ground plane.
  You will need to change the WRAP parameters for `s` and `t` and you will need to change the texture coordinates of the ground plane.
  Look at initGeom and look at the appropriate: `glTexParameterf` call.

3. Now create a new fragment shader and apply it to one of the textured meshes (for example the world).
  Do something creative per pixel – for example, stop drawing the fragments associated with the ocean or add a specular component to the ocean only.
  Be creative.
  The effect must be clearly discernable.

Example output showing a modified world shader and the ground texture improved is shown below.
You can also play with the dog model included in the base code if you’d like.

{% include image-block.html file="lab9_3.png" alt="Lab 9 Figure 3" %}
