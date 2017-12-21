---
layout: page
active: lectures
title: "Lecture 20: Framebuffers"
auto-title: true
---


## Framebuffers

Framebuffers are used when we want to draw somewhere other than the screen.
If you bind a framebuffer, then any subsequent draw call will draw onto the framebuffer.

Typically, we attach a color texture and a depth texture to a framebuffer.
Thus the color of every fragment rendered will end up in the attached texture,
and the depth values will end up in the attached depth texture.

### Renderbuffers

If we don't care to access the values of a framebuffer attachment,
we can attach a renderbuffer instead of a texture.

The most common use of this is for depth -
we very commonly want a depth buffer, but typically don't need to actually read these values back.

### Ping Pong

You can't read and write to the same buffer in a single draw call.
So if we want to do any sort of multi-pass rendering (e.g. a blur),
we need to create two framebuffers and "ping pong" in-between them.

