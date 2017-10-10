---
layout: assignment
assignment: "lab07"
title: Lab 7
---

<div class="alert alert-dismissible alert-danger">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <h4>Warning!</h4>
  <p>
    This content is not fully ready yet.
    The details of the assignment may change, and build instructions and base code may not yet be available!
  </p>
</div>

Simple lighting – diffuse lighting on a sphere

Today we will implement simple diffuse lighting for a sphere obj file. Starting with any
prior lab code that reads in an obj file (including the mesh normal), you will add the
necessary code to shade the mesh with diffuse lighting. For this lab, you will need to
modify both the .cpp file and the vertex shader.



## Task 1

Change the code to read in a sphere mesh and alter the drawing so that you can draw two
spheres side by side that are rotating around the Y axis.



## Task 2

Now modify the vertex shader (and .cpp file as necessary) to shade the sphere with
Gouraud diffuse and ambient shading (this means that you will compute the color in the
vertex shader).

1. You can choose a fixed light position to use to compute the light vector
2. You can choose two different diffuse colors for each sphere
3. For one sphere, update the normal to follow the rotation
4. For the other sphere, leave the normal as they are (so the lighting stays ‘fixed’
  or painted on the sphere)

An example of a single frame would look as follows:

{% include image-block.html file="lab7_1.png" alt="Lab 7 Figure 1" %}



## Task 3

Now modify the vertex and fragment shader (and .cpp file as necessary) to shade the
sphere with Phong diffuse and ambient shading (this means you will compute the color in
the fragment shader with an interpolated normal – you will also need to pass in an
interpolated light vector).

An example of a single frame would look as follows:

{% include image-block.html file="lab7_2.png" alt="Lab 7 Figure 2" %}
