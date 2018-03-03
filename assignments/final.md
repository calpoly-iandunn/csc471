---
layout: page
active: assignments
title: "Final Project"
auto-title: true
---

<p><a href="https://classroom.github.com/a/dLRmHrl4" class="btn btn-info">GitHub Classroom - Proposal</a></p>
<p><a href="https://classroom.github.com/a/-NdAZ3Vw" class="btn btn-info">GitHub Classroom - Code</a></p>
<p><a href="https://classroom.github.com/a/aHeB6af4" class="btn btn-info">GitHub Classroom - Website</a></p>

## Overview

Your final project for this class is very open ended.
The essential requirement is that I want you to make an **interesting** graphics application.

A few possibilities:

* Pick a handful<sup>[1]</sup> of technologies to use to create a visually interesting or otherwise creative scene.
* Do a simulation of something - gameplay, or something scientific/physical - and display the simulation.
* For some other topic not related to computer graphics, create an interesting 3D visualization.
* Pick a difficult or advanced computer graphics topic and implement it correctly (with tools to help debug and verify that technology).

And these possibilities are not mutually exclusive!

**\[1\]**: How many is a handful? Generally speaking two (especially for simple technologies), but it depends on how much the technology is explored or expanded upon,
and the other aspects of your project (i.e. creative aspects, any sort of simulation or gameplay, complexity of the scene).

I know that it is difficult to guage whether a project idea meets my personal critera of **"interesting"** or not.
That's why, during the last two weeks of the quarter, I will meet with everyone in lab to discuss project ideas and implementation progress.

It is also *especially* helpful to browse through [Zoe's extensive history of past 471 student final projects](http://users.csc.calpoly.edu/~zwood/teaching/csc471/top_final.html)
as well as [the final projects from my last quarter of 471](http://users.csc.calpoly.edu/~idunn01/teaching/csc471/finalf17/).

### Technologies

This is not an exhaustive list.

#### Essential

These are the technologies that we focused on as part of this class.
These can either be included as one of the aspects of your final project,
or expanded/deepened upon (with some ideas given after each technology).

* Hierarchical Model: Complex hierarchy with interesting animation
* Lighting: More light sources, more types of light sources, different BRDF equations
* Camera control: character controller, "camera on a spring", 6 degree-of-freedom
* Texture mapping: Interesting use of multiple textures per object
* Particles: Animated effect (e.g. explosions), advanced emitters/effectors, transform-feedback


#### Standard

These are just some general technologies that we didn't cover in the class,
but can definitely be explored for a final project.

Some difficulty labels have been applied but they are very approximate -
the difficulty of a technology depends on the depth to which the technology is explored,
and the degree to which the technology is self-implemented versus followed from a tutorial.

* Terrain heightmap **[Simple]**{: style="color: MediumSeaGreen"}
* Skybox/skysphere **[Simple]**{: style="color: MediumSeaGreen"}
* Underwater caustics
* Reflective and/or refractive water surface
* Editable terrain heightmap **[Moderate]**{: style="color: GoldenRod"}
* Rigid body animation
* Collision detection
* Sound/audio
* Artifical intelligence
* Game mechanics
* Bitmapped text
* Environment mapped reflections
* Image-based lighting
* Curve interpolation (i.e. spline animation)
* Perlin noise (or simplex noise) **[Simple]**{: style="color: MediumSeaGreen"}
* Geometry shaders
* Simple shadows (planar shadows or projected textures)
* Boids (flocking algorithm)
* Physically-based BRDF such as Cook-Torrance **[Moderate]**{: style="color: GoldenRod"}


#### Advanced

Advanced technologies can be difficult to implement,
usually due to the complexity of debugging them when they go wrong.

* Deferred shading **[Advanced]**{: style="color: Tomato"}
* Skinned mesh animation **[Advanced]**{: style="color: Tomato"}
* Screen-space ambient occlusion **[Advanced]**{: style="color: Tomato"}
* View-frustum culling **[Advanced]**{: style="color: Tomato"}
* Advanced Shadows (either shadow maps or shadow volumes) **[Advanced]**{: style="color: Tomato"}


## Dates

Dates to watch out for:

- Meet with instructor during lab to finalize project choice **{{ site.data.dates[0].when }}**

- Submit short (1-2 paragraphs) description of project **{{ site.data.dates[1].when }}**

- Required in lab project check-in: **{{ site.data.dates[2].when }}** and **{{ site.data.dates[3].when }}**
  (should be able to demonstrate some progress on the project)

- Final project demos in final exam time period

All dates are also on the course schedule and the calendar.



## Project Proposal

For the project proposal, you need to submit a 1-2 paragraph written description of your project.
You will need to include a brief overview of the project and a list of the project’s goals.
Be sure to think about and include information on such topics as:

- what kind of data is necessary for your project (what is the input data type and output data type)

- where you will be getting any data you may need

- what resources/references you will use or may need

- how the user will interact with your program and what you will ultimately display/render.

Please include any references you have already found.
In general, the format of your project description should include:

- Introduction: general description of the project

- Goals: list of what your project will accomplish (this can be a bullet list)
  (you do not need to include a timeline, but I encourage you to think about a timeline and include it if you’d like).

- **Highlight what graphics technology you will either be deepening your knowledge of or expanding your knowledge of.**

- Any references

Feel free to include any figures that will help illustrate your project if relevant.
For ideas for a project, consider looking at all the past class projects or at the SIGGRAPH website for past papers, sketches and courses.

### Hand-In

[Submit your final project description via GitHub Classroom at this link.](https://classroom.github.com/a/dLRmHrl4)

The following formats are acceptable:

- PDF (`.pdf`)
- Markdown (`.md`)
- Plain text (`.txt`)



## Final Deliverables

You will be doing an in class 5 minute presentation of your project – demonstrating the accomplishments of your project to your peers and the professor.
Please note that you will need to submit the source code, executable, and relevant data related to your final project to Github Classroom before the scheduled final time.

In addition, you will need to submit a webpage documenting your project (include project description, results images, and references on the webpage).
The website is due at the same time as the final project and will be turned in via Github Classroom.

Your final project website must consist of `.html` and `.css` files.
It must link to either images or videos of your project.
Please also include one image that you would like to be the thumbnail for your project, called `thumbnail.jpg` (or `.png` or `.gif`).


---

Projects will be classified as: easy, medium or hard.
An easy project can earn at most 90 points, a medium project can earn at most 100 points, a hard project can earn 110 points.

General point break down:

- **10** Project proposal and write-up
- **10** Progress check-in (these act as multipliers on your grade or either 1, 0.5 or 0)
- **70-90** Project completion, demonstration, and webpage

### Hand-In

[Submit your final project code via GitHub Classroom at this link.](https://classroom.github.com/a/-NdAZ3Vw)

[Submit your final project website via GitHub Classroom at this link.](https://classroom.github.com/a/aHeB6af4)
