---
layout: page
active: syllabus
title: Syllabus
---


# Syllabus for CSC 471: Introduction to Computer Graphics

* **Instructor:** Ian Dunn
* **Office:** Building 14, Room 209
* **Office Hours:** [See here](https://calpoly-iandunn.github.io/)
* **Email:** idunn01@calpoly.edu
* **Schedule:**
  * Lecture: MWF {{ site.data.course.meetings.lecture.when }} ({{ site.data.course.meetings.lecture.in }})
  * Lab: MWF {{ site.data.course.meetings.lab.when }} ({{ site.data.course.meetings.lab.in }})
* **Website:** [https://iondune.github.io/csc471/](https://iondune.github.io/csc471/)

## Overview

### General:

Welcome to computer graphics.
This course will teach you the fundamentals for writing your own interactive computer graphics applications.
This course requires substantial math and programming skills.
Experience with C or C++ will be essential and experience with linear algebra will be helpful.

### Development Environment:

We will be using

* C++ as the main language
* OpenGL/GLSL as the graphics API
* GLFW for windowing, mouse/keyboard input
* glm for matrix operations
* CMake for cross-platform compilation and development

All your programs must compile in the CSL (but you may develop under other operating systems).
I expect you to be curious about creating interactive visual computing artifacts with algorithms and math,
along with being willing to experiment and learn on your own to create interesting computer graphics programs.

### Course Objectives, by the end of the quarter students will:

* Understand the graphics pipeline and the basic implementation of the pipeline in modern hardware (and graphics libraries)
* Understand and be able to apply coordinate transforms and affine transformations and understand the application of such transforms using a vertex shader
* Understand and be able to apply basic geometric computations involving points, lines, planes and triangles related to spatial queries
* Be able to program basic data structures to represent a mesh (including applying transforms and necessary data for shading)
* Understand rasterization (algorithm, stage in the graphics pipeline, and relationship to fragment shaders)
* Understand basic hierarchical animation
* Understand and be able to write local shading models (Phong, etc.)
* Understand and be able to apply basic texture mapping
* Be introduced to the application of more advanced computer graphics (including rendering, animation, real time and visualization)
* Practice translating mathematics into C/C++ programs

### Final grade breakdown:

* 10%: 10 Lab exercises
* 45%: 4-6 Programming assignments
* 20%: 2 midterms
* 20%: One larger final programming project
  * project must be approved by the instructor (details to follow)
* 5%: Participation and in class quizzes

Your latest grade information will always be available on PolyLearn,
which should have the above weighting implemented.


## Course Details

### Labs:

Each lab exercise is typically due within three lab sessions, but the due date for each assignment is posted on the schedule.
For example, typically if a lab is assigned on Monday, it must be completed by the end of Friday's lab.
Labs must be checked off by me or the TA during the lab unless you have my prior permission.

Labs can be turned in one **course day** late for 70% credit.
So if a lab is due on Friday, it can be turned in on Monday for a maximum of 70%.

Labs can also be turned in two **course days** late for a maximum of 30% credit.
After that, late labs will not be accepted.

### Assignments:

There will be 5 substantial individual programming assignments.
If your program is late you will lose 20% within first 24 hours after deadline, 40% within 48 hours, 100% after 48 hours.
However, you get 2 *free* days for the entire quarter which can be applied to the four programming assignments only.
You do not need to explain why you are using the days - these two late days will be automatically applied to any late assignments.
After your two late days have been used up, the late penalties apply.

Late days are to be used for any and all reasons you might need to turn in an assignment late, including job interviews and travel.

Assignments will be turned in using GitHub Classroom.

### Midterms:

There will be 2 written midterm exams.
You may bring a double-sided sheet of hand-written notes to both midterms.

In an attempt to make the exam grading process more transparent and fair, and to simply reduce the grading work,
I will be using gradescope to grade your midterm exams.
Once exams are graded you can review the results, including the problem rubric, by logging in to gradescope.

If for whatever reason you don't want to sign up in order to view your exam,
just let me know via email and I'll generate a PDF copy with your results.

### Project:

You will get roughly 3 weeks at the end of the quarter to work on the final project.

### Recommended (optional) texts:

Please consider *Fundamentals of Computer Graphics* by P. Shirley or *Foundations of 3D Computer Graphics* by S. Gortler.
For a reference for modern graphics programming:
*OpenGL ES 3.0 Programming Guide* by D. Ginsburg, et. al.

There are also numerous helpful tutorial sites for example:

- [http://learnopengl.com/](http://learnopengl.com/)
- [http://ogldev.atspace.co.uk/](http://ogldev.atspace.co.uk/)
- [http://www.opengl-tutorial.org/](http://www.opengl-tutorial.org/)

### Participation:

I expect you to participate in class and engage with the class material
(studies suggest that taking longhand notes is one of the better ways to guarantee your engagement with the material in class) **[1]**.
I also expect you to form a community of scholars for the duration of the quarter (and hopefully longer).
My teaching style is very interactive – if you want to know more about why see **[2]**.
Laptops have been shown to be distracting in lecture **[3]** and are not allowed unless specified (or a specific exception is negotiated) - same for cell phones.
There also might be random pop quizzes during the class as a part of participation.

### Honesty:

Although I encourage you to have lively discussions with one another, _all work you hand in must be your own work_.
If your program or parts of your program are plagiarized from another student or unapproved sources including tutorials,
you will fail the course and a letter will be put in your file with Cal Poly Judicial Affairs.
Note some old tutorials do not use modern graphics &mdash; if you use them, this can result in problems.
You can talk to one another about your solutions and you may look at another student's code that has a bug (I encourage you to help each other with de-bugging),
but you cannot look at someone else's working code.

Note that I expect your OpenGL code to conform to at least OpenGL 3.0 standards (sometimes referred to as "modern graphics") -
some specifics include no use of immediate mode for rendering and no OpenGL matrix stack calls (instead we will be using glm for a matrix library)
and all shading will be computed using GLSL shaders.
Your code must compile and run on the machines in the CSL.

#### References
- **[1]** [http://www.theatlantic.com/technology/archive/2014/05/to-remember-a-lecture-better-take-notes-by-hand/361478/](http://www.theatlantic.com/technology/archive/2014/05/to-remember-a-lecture-better-take-notes-by-hand/361478/)
- **[2]** "Applying the Seven Principles for Good Practice in Undergraduate Education" (1991) Chickering and Gamson
- **[3]** [http://www.yorku.ca/ncepeda/laptopFAQ.html](http://www.yorku.ca/ncepeda/laptopFAQ.html)
