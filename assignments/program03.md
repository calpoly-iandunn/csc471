---
layout: assignment
assignment: "program03"
title: Program 3
---

<div class="alert alert-dismissible alert-danger">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <h4>Warning!</h4>
  <p>
    This content is not fully ready yet - we will be adding a few more things.
    Base code, if any, is not yet available!
  </p>
</div>

The late policy on the syllabus applies. This programming assignment
should be done individually! You may talk to one another about the program, but you
may not look at someone’s working code.



## Objectives

Learn about handling obj files with multiple shapes and shading, specifically
the Blinn-Phong model, and explore creating appealing materials. Goal: create a program
that can set up a scene with multiple meshes with different material properties on the two
different meshes.

You may start with any of the prior code to read in an obj mesh, but I recommend the
program 3 release code.



## Step 1:

Fix the base code to be able to display a mesh from an obj file with multiple
“shapes. By default the older code we have worked with on displayed “shape[0]” from
the obj file. The new base code is set up so that you can create a “Shape” object for each
of the tiny_obj “shapes” . You need to fix the code in “initGeom” in main.cpp and you
need to compute the bounds of the entire mesh to make sure it can display at the origin
and a reasonable scale. Once you have this code in place, you should be able to see thw
whole “dummy” model. See the below figure for an example:

{% include image-block.html file="program3_1.png" alt="Program 3 Figure 1" %}



## Step 2:

Write code to compute the Blinn-Phong lighting model for your mesh.

---

You will need to add code to specify lighting in your world. Your program
should have at least one light source at a reasonable position (Please have at least
one light start at `position = {-2, 2, 2}` that is white `color = {1, 1, 1}`).

Allow the user to change the
position of the light using the keyboard – specifically if the user presses the `q`
key the light should move to the left and when the user presses the `e` key the
light should move to the right. All lighting should be done via your GLSL
shaders. You may implement more complex lighting options that you can define
in your readme.

---

You will need a way to specify different materials for the mesh (which will
control its shading). Three default materials are provided below in a helper
function– you must include these in your implementation these as your lighting
results will be compared against these. You will need to add another material that
you find interesting. Provide support to toggle through all four of the different
material via the `m` key.

---

Next implement the Blinn-Phong shading in your fragment shader (i.e. the
normals are interpolated across the face and shading is computed per pixel). Note
there are several tutorials on this. We are familiar with the tutorial code and will
notice it if you hand it in as your own. Please write your own code from scratch
and understand what each line is doing.

---

*Be sure you keep all vectors in the same space!* No vectors used for lighting
should be transformed in perspective space.

---

Add basic mesh transforms such that the `a` and `d` keys hooked up to rotate the
left most mesh around the Y axis.

In general, set up a scene with at least two meshes. Either the same one in two different
positions (with two different materials) or two different meshes. For extra credit, figure
out which shapes in the model belong to which parts and transform part of the model (see
below figure where the upper torso of the dummy has been rotated in two different
directions).

When not specified exactly, you must make reasonable design choices as to exactly how
to support the necessary functionality for the program.



## Grading

Point breakdown (A completely functional program is worth 100 points total):

- 30 pts for a multi-shape mesh
- 30 pts for correct Blinn-Phong fragment shader
- 15 pts for translating the light
- 15 pts for correct (and unique new) materials
- 10 point for overall functionality (i.e. functioning transformations, etc.)

{% include image-block.html file="program3_2.png" alt="Program 3 Figure 2" %}


```cpp
void SetMaterial(int i) {
  switch (i) {
  case 0: // shiny blue plastic
    glUniform3f(prog->getUniform("MatAmb"), 0.02, 0.04, 0.2);
    glUniform3f(prog->getUniform("MatDif"), 0.0, 0.16, 0.9);
    glUniform3f(prog->getUniform("MatSpec"), 0.14, 0.2, 0.8);
    glUniform1f(prog->getUniform("shine"), 120.0);
    break;
  case 1: // flat grey
    glUniform3f(prog->getUniform("MatAmb"), 0.13, 0.13, 0.14);
    glUniform3f(prog->getUniform("MatDif"), 0.3, 0.3, 0.4);
    glUniform3f(prog->getUniform("MatSpec"), 0.3, 0.3, 0.4);
    glUniform1f(prog->getUniform("shine"), 4.0);
    break;
  case 2: // brass
    glUniform3f(prog->getUniform("MatAmb"), 0.3294, 0.2235, 0.02745);
    glUniform3f(prog->getUniform("MatDif"), 0.7804, 0.5686, 0.11373);
    glUniform3f(prog->getUniform("MatSpec"), 0.9922, 0.941176, 0.80784);
    glUniform1f(prog->getUniform("shine"), 27.9);
    break;
  }
}
```
