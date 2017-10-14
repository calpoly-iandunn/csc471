---
layout: page
active: lectures
title: "Lecture 15: Lighting 1"
auto-title: true
---

Why do we care about lighting?

Lighting makes things look 3D.

Without lighting:

![flat-sphere](15-figure-flat-sphere.svg)

With lighting:

![shaded-sphere](15-figure-shaded-sphere.png)

Some definitions:

**Shading:** the process of assigning a colors to pixels

**Illumination:** the transport of photons from light sources via direct and indirect paths


## Color and Light

**Light** is both a wave and a particle.
That's just some quantum mechanics nonsense.
But in computer graphics we are concerned with some of the details that arise from this.

First, the **wavelength** of this wave tells us the color of the light.
Visible light ranges from 450nm to 700nm.
450nm is {% include color-text.html color="#92d;" label="violet" %} and 700nm is {% include color-text.html color="red" label="red" %}.

Light is characterized by its spectrum: the amount of energy at each wavelength.

This is a full distribution: one value per wavelength (infinite number of values).

![color-signal](15-figure-color-signal.png)

To understand light and illumination, we need to understand two things.

**(1)** How does light get to our eyes (what happens on the way)?

**(2)** What happens when light hits our eyes?


Let's talk about the second part, then go back to the first part.


## Color Vision

### Simple and Ultimately Wrong Version

You have red, green, and blue cones.
Red cones see red light, green cones see green light, blue cones see blue light.

If you see {% include color-text.html color="red" label="red" %} and {% include color-text.html color="green" label="green" %},
your brain says "{% include color-text.html color="#cb1" label="yellow" %}!"

This is a (reasonable) guess based on how yellow is inbetween red and green in the spectrum.

All of {% include color-text.html color="red" label="red" %}, {% include color-text.html color="green" label="green" %}, and {% include color-text.html color="blue" label="blue" %} cones? White.

None of the cones? Black.

Just {% include color-text.html color="green" label="green" %} and {% include color-text.html color="blue" label="blue" %}? {% include color-text.html color="#14dde8" label="Cyan" %}.

{% include color-text.html color="red" label="Red" %} and {% include color-text.html color="blue" label="blue" %}? {% include color-text.html color="green" label="Green" %}.

Wait...

Our brains know that something is up when we see red and blue at the same time.
The middle is green... but instead our brain makes up a color.
{% include color-text.html color="#c19" label="Pink" %}!

Pink is not on the spectrum.

Pale red and pale violet are... but a mix of these colors is not on the spectrum.

That doesn't mean that Pink isn't a color, though.
Color is just the word we use to describe how our brains interpret light.
Pink is one of the ways that our brain interprets light, so it's a color.
It is called a [non-spectral color](https://en.wikipedia.org/wiki/Spectral_color#Non-spectral_colors).


### Now a More Accurate Version

You have eyes.

![eye-diagram](15-figure-eye-diagram.png)

In your eyes there are cones.

![cone-diagram](15-figure-cone-diagram.png)

There are three types of cones but they are not as simple as red, green, and blue.
They are called L, M, and S cones and they each have sensitivity to certain frequencies.

![cone-sensitivity](15-figure-cone-sensitivity.png)

There is some overlap between different sensitivity regions.
But the "cones" don't see anything.
They just relay information to your brain.
Your brain has to take this information and deduce what color you are seeing.



### Cone Response

