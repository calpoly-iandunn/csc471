---
layout: page
active: references
title: "Debugging OpenGL Applications"
auto-title: true
---



## OpenGL Errors

Every OpenGL function has a chance to fail and produce an error code.
However, the error is not reported - it is simply saved in a global variable.
[`glGetError`](http://docs.gl/gl4/glGetError) can be used to retrieve this error code.
The error codes are typically not very useful - typically you see either
`GL_INVALID_OPERATION` or `GL_INVALID_ENUM` which doesn't tell you a whole lot about the problem.
However, if something is going wrong it is typically useful to know *which* OpenGL call produced the error.

Unfortunately, the only way to know which OpenGL call produced an error is by checking for errors immediately after.
And even this only tells you whether any previous call produced an error, not whether a specific call did.
The only way to reliable determine which OpenGL call produced an error is to check for errors after *every single call*.

This can be facilitated through a C++ [macro](http://en.cppreference.com/w/cpp/preprocessor/replace).
We provide one in the base code for all OpenGL assignments, in [GLSL.h](https://github.com/calpoly-csc471/lab03/blob/master/src/GLSL.h#L32): `CHECKED_GL_CALL`.
The macro itself is not important, but if you put it around every OpenGL call it will automatically report every error that occurs.
It will also report if an error was produced **before** the wrapped OpenGL call.

If you've ever seen a message like this:

```
OpenGL error in file 'Program.cpp' at line 93 calling function 'BEFORE glUseProgram(pid)': 'Invalid operation' '1282 0x502'
```

Here, the `BEFORE` indicates that the macro checked for an error *before* calling the OpenGL function and discovered that an error was already waiting to be reported.
Since we don't use the `CHECKED_GL_CALL` macro in `main.cpp`, if an error is produced there it is usually not detected until some code elsewhere, like `Program.cpp` checks for errors.

What we can do is add the error checking to our code to figure out where the problem is.
For example, if we just added these lines, we could error-check them:

```cpp
glEnableVertexAttribArray(0);
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 0, (void*) 0);
glBindVertexArray(0);
```

... becomes ...

```cpp
CHECKED_GL_CALL(glEnableVertexAttribArray(0));
CHECKED_GL_CALL(glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 0, (void*) 0));
CHECKED_GL_CALL(glBindVertexArray(0));
```

If the error comes from one of these calls, we would see it in the console.




## OpenGL Debug Messages

There is an OpenGL extension ([KHR_DEBUG](https://www.khronos.org/registry/OpenGL/extensions/KHR/KHR_debug.txt))
that enables the automatic reporting of OpenGL errors (without having to manually check, like above)
as well as other diagnostic and performance messages.

However, being an extension, it is not necessarily supported by all hardware and platforms.
In particular, as of now it is currently still unsupported on all OS X devices.

However, if you are on Linux or Windows and have somewhat recent hardware, it should be available.

[See this Gist for some example usage and a sample callback function.](https://gist.github.com/iondune/59e5d9a6d0b9edfa85fa35c957961371)

