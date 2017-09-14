---
layout: page
active: assignments
title: "Lab 1"
---

# Lab 1 - Software Rasterizer: Bounding Box

<div class="alert alert-dismissible alert-danger">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <h4>Warning!</h4>
  <p>
    This content is not fully ready yet.
    The details of the assignment are not likely to change, but build instructions and base code might be changing soon!
  </p>
</div>


You must work individually.

Please download the code for the lab and go over the code.

- On the web: [http://users.csc.calpoly.edu/~zwood/teaching/csc471/2016F/Labs/L01/L01.zip](http://users.csc.calpoly.edu/~zwood/teaching/csc471/2016F/Labs/L01/L01.zip)
- On the server: `cp ~zwood/www/teaching/csc471/2016F/Labs/L01/L01.zip .`


## Overview and Context

Over the next 2 weeks, we will be writing a program to render (draw) an indexed face set (aka polygonal mesh of triangles) as an image via software rasterization
(i.e. the code will be entirely written in C/C++ with no graphic libraries. The software will render a static scene).
In general the required steps for the program will be:

- Read in triangles.
- Convert triangles to window coordinates.
- Rasterize each triangle (using barycentric coordinates for linear interpolations and in-triangle test).
- Write color values per pixel (using a z-buffer test to resolve depth).

We will discuss the window coordinate transform, barycentric coordinates and z-buffers in the next few lectures.


## Goals for Today's Lab
For today, we will just be playing with the provided image code to build up functionality that will be useful in your rasterizer.

- Set up g++ and CMake.
- Read in three vertices which represent a triangle (see below for details).
- Color all the pixels in the bounding box the color of your choice.
- Write out those pixels as a PNG image (base code provided).


### Step 1
We'll be using g++ and CMake throughout this quarter.
We'll also be using "out of source" builds.
If you're using the lab machines, g++ and CMake are already installed.
To compile and run your code from the command line, follow these steps from the folder containing CMakeLists.txt.

```
> mkdir build
> cd build
> cmake ..
> make -j4
> ./Lab01
```

You should see some output on the console.
Look at `main.cpp` to see what the command line arguments mean.
Once you enter the correct arguments, you should see the following output file in the build directory.

![lab1_1](lab1_1.png)

If you're using your own computer, follow the steps below to install g++ and CMake.
Otherwise, you can skip to Step 2.


#### Linux

Use a package manager to download cmake. For example, with ubuntu,

```
> sudo apt-get update
> sudo apt-get g++
> sudo apt-get install cmake
```

Follow the steps above to build and run the program from the command line.


#### OSX

You can use homebrew/macports or install these manually.

- Xcode developer tools. You'll need to log in with your Apple ID.
- CMake ([http://cmake.org/download/](http://cmake.org/download/))

Make sure the commands g++ and cmake work from the command prompt.
If you want to use Xcode as your IDE, then do the following from the folder containing CMakeLists.txt.

```
> mkdir build
> cd build
> cmake -G Xcode ..
```

This will generate Lab01.xcodeproj project that you can open with Xcode.
To run, change the target to Lab01 by going to Product -> Scheme -> Lab00.
Then click on the play button or press `Command+R` to run the application.
Edit the scheme to add command-line arguments or to run in release mode.


#### Windows

You'll need to download these manually.

- Visual Studio. Any version should work.
  I've tested Visual Studio 2015 (aka version 14) on Windows 8.
- CMake ([http://cmake.org/download/](http://cmake.org/download/)).
  Make sure to add CMake to the system path when asked to do so.

Make sure the command cmake works from the command prompt.
On Windows, you'll be using Visual Studio as the IDE.
Run the following from the folder containing CMakeLists.txt. to generate a solution file.

```
> mkdir build
> cd build
> cmake ..
```

By default on Windows, CMake will generate a Visual Studio solution file, Lab01.sln, which you can open by double-clicking.
If you get a version mismatch, you may have to specify your visual studio version, for example:

```
> cmake -G "Visual Studio 14 2015" ..
```

Other versions of Visual Studio are listed on the CMake page ([http://cmake.org/cmake/help/latest/manual/cmake-generators.7.html](http://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)).

- To build and run the project, right-click on Lab01 in the project explorer and then click on "Set as Startup Project."
  Then press F7 (Build Solution) and then F5 (Start Debugging).
- To add a commandline argument, right-click on Lab01 in the project explorer and then click on "Properties" and then click on "Debugging."


### Step 2

Starting with the provided code, make the list of command line arguments take the following options (in exactly this order)

- Output filename (e.g., foo.png)
- Image width (e.g., 512)
- Image height (e.g., 512)
- Vertex 1 x-coord (e.g., 100)
- Vertex 1 y-coord (e.g., 100)
- Vertex 2 x-coord
- Vertex 2 y-coord
- Vertex 3 x-coord
- Vertex 3 y-coord

**Usage:** `Lab01 filename width height vax vay vbx vby vcx vcy`

Thus for example – a valid program execution would look like:

```
./Lab01 out.png 200 200 2 2 50 60 150 170
```

For today only, we will assume the triangle's vertices are in "window coordinates."
In other words, the data values are integer values that range from 0 to the value of width-1 of the window/image (or 0 to the height-1 value of the window/image).
You may choose to have the vertices be 2D (although for the Assignment 1, they will need to be 3D).
You will need to design a data structure to represent the triangle and its vertices.
Draw the three vertices into the image, using three calls to image->setPixel().

The bounding box of the triangle is the box with the extents that will exactly bound that triangle.
You will need to design a data structure to represent the bounding box.
At minimum such a structure needs xmin, xmax, ymin, ymax. Using the provided image code, modify the color of all the pixels in the bounding box to be a color of your choice (which is different then the background).

You can also try a pattern based on the row and/or column.
The three vertices and the bounding box should look something like this:

![lab1_2](lab1_2.png)

Write out the modified image and confirm your code is working as expected.
Be sure to try various test cases with vertex positions in various orders.
Make sure the bounding box completely covers the three vertices.

## Lab check

For lab credit you will need to demonstrate your working code on several vertex tuples specified by the instructor or the TA.
