---
layout: page
active: references
title: "Midterm 1 Guide"
auto-title: true
---


The following topics *could* appear on midterm 1.
This list could shrink or expand (which would be announced in class).

**You will be able to bring one hand written single or double sided sheet of notes into the exam**


### 2D coordinate transforms

- understand in general why we use different coordinate systems (world, image and pixel)
- be able to solve for the scale and translate variables of a mapping from one 2D coordinate system to the next, given corner constraints


### Vectors

- understand how to do vector addition, subtraction, scalar multiplication, dot product and cross product
- understand how to find the angle between two vectors
- understand the difference between a vector and a point
- understand the relationship of vectors, points and planes


### 3D transforms and matrices

- have a general understanding of matrices and matrix/vector operations
- understand what matrices look like for various 2D and 3D transformations, such as translation, scale, rotate and shear
- be able to apply these transforms
- Write the pseudo-code for the virtual trackball rotations.
- Be able to clearly specify what a composite transform will do to given geometry


### OpenGL/GLSL/glm

- Understand the role of a vertex shader
- Understand the role of a fragment shader
- Understand basic GLSL coding (data passing and computation)
- Understand the basic structure and reasoning for using vertex buffer objects (VBOs) and index buffer objects (IBOs)
- know general OpenGL/GLSL/glm calls for drawing basic primitive types and for applying transformations


### Rasterization

and depth buffer algorithms


## Sample Questions


### 2D Coordinate Transforms

Assume that we have world coordinates defined as follows:

$$ left = -w/h $$

$$ right= w/h $$

$$ top = 3.0 $$

$$ bottom = -3.0 $$

![figure-01](midterm-1-figure-1.svg)

We would like to map these coordinates to pixel coordinates for a window with the following coordinate values:

![figure-02](midterm-1-figure-2.svg)

Assuming that we know that the mapping will contain a scale and translate and thus be of the form:

$$ x_p = c*x_w + d $$

$$ y_p = e*y_w + f $$

Solve for $$c$$, $$d$$, $$e$$, and $$f$$.
Hint: writing out the constraints -
for example we know that when we send left through the mapping we want it to equal $$0$$,
i.e., $$ 0 = c*(-w/h) + d $$

How is the pixel coordinate system different then the world coordinate system?
How do we make sure that a circle in the world coordinate system does not get drawn as an ellipse in the pixel coordinate system?


### Vectors

Given the following vectors:

$$ v^T = \begin{bmatrix}1 & 4 & 6\end{bmatrix} $$

$$ u^T = \begin{bmatrix}0 & 1 & 4\end{bmatrix} $$

$$ w^T = \begin{bmatrix}10 & 3 & 5\end{bmatrix} $$

and the scalar $$ s = 4 $$

Compute:

**1.** $$ v - u $$

**2.** $$ u + w $$

**3.** $$ s * u $$

**4.** $$ v \cdot u $$

**5.** what is the angle between $$v$$ and $$w$$ (don’t compute it just write solution in terms of $$cos$$)

**6.** what is the projection of $$u$$ onto $$w$$

---

Given the points $$ p_0 = \{ 1,  0 \} $$ and $$ p_1 = \{4, 6\} $$
write the implicit equation for a line in vector form (i.e. compute the appropriate $$v$$ and $$n$$).

Is the point $$ p_2 = \{ 1.5, 3 \} $$ on the line or above or below the line?

---

What is the equation for a plane with the normal $$ n^T = \begin{bmatrix}5 & 3 & 4\end{bmatrix} $$ going through the origin?

What is the equation for the planes with the same normal but which include the point $$ p_1 = \{ 4, 6, 7 \} $$?


**More problems coming soon**


## Prior Exam

[Prior Exam - Winter 2017](midterm1_W17.pdf) will be posted after the first student-hosted, public study session!

