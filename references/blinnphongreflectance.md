---
layout: page
active: references
title: "Blinn-Phong Reflectance Model"
auto-title: true
---


## Formula

In the **Blinn-Phong Reflectance Model**, reflectance is defined as:

$$ I_T = I_A + \sum_{i=0}^n I_D + I_S $$

For $$ n $$ lights where:

$$ I_T $$ is the total reflectance.

$$ I_A $$ is the ambient reflectance.

$$ I_D $$ is the diffuse reflectance for a given light.

$$ I_S $$ is the specular reflectance for a given light.

To compute these components, we need to define a few vectors.



## Vectors

{% include image-block.html file="blinnphong.svg" alt="Blinn-Phong Reflectance Vectors" %}

All vectors used should be normalized.

$$ \vec N $$ is the surface normal.

$$ \vec L $$ is the light vector, pointing from the surface towards the light.

$$ \vec V $$ is the view vector, pointing from the surface towards the viewer (camera).

$$ \vec H $$ is the half vector, halfway between the $$ L $$ and $$ V $$ vectors.
It can be computed by $$ \frac{L + V}{||L + V||} $$

Note that we are not concerned with $$ \vec R $$, the Reflection vector, for the Blinn-Phong model.



## Components

All dot products used should be clamped between $$ 0 $$ and $$ 1 $$.

### Ambient

$$ I_A = k_a $$

### Diffuse

$$ I_D = k_d * (\vec N \cdot \vec L) $$

### Specular

$$ I_S = k_s * (\vec H \cdot \vec N)^\alpha $$



## Implementation

$$ k_a $$, $$ k_d $$, and $$ k_s $$ are the material properties.
They should be `vec3` (colors).

$$ \alpha $$ is also a material property, sometimes called `shininess` or lower-case `n`.
It is a scalar.

Don't forget to:

- Normalize all vectors
  - Vectors passed from the vertex shader to the fragment shader should be normalized both before and after passing.
    The interpolation of two or more normalized vectors is not guaranteed to be normalized.
- Clamp all dot products between $$ 0 $$ and $$ 1 $$

Note that the equation $$ \frac{L + V}{||L + V||} $$ does not mean you actually need to divide by the length of $$ L + V $$.
This is merely the notation for a normalized vector.
You should simply write in GLSL:

```glsl
vec3 H = normalize(L + V);
```
