---
layout: page
active: references
title: "Camera Controls"
auto-title: true
---


To implement camera controls for a pitch and yaw camera, there are two components.
First, you must map mouse controls to the pitch and yaw (phi and theta) angles of the camera.
Second, you must map keyboard controls to the movement of the camera.

Below is some sample to code to show you how to set up these controls in a way that I think is most effective for 3D graphics demos.
First, we will implement "click-and-drag" movement of the camera angles.
Then, we will set up smooth camera position movement.


## Camera Angles

We want to only use the cursor movement to adjust the angles when the mouse is clicked down.
This means we need to keep track of when the mouse is clicked, as well as wherever the cursor was the last time it moved.

```cpp
float cTheta = 0;
float cPhi = 0;
bool mouseDown = false;

double lastX = 0;
double lastY = 0;
float cameraRotateSpeed = 0.005f;

void mouseCallback(GLFWwindow *window, int button, int action, int mods)
{
  if (action == GLFW_PRESS)
  {
    mouseDown = true;
  }

  if (action == GLFW_RELEASE)
  {
    mouseDown = false;
  }
}

void cursorPosCallback(GLFWwindow* window, double xpos, double ypos)
{
  if (mouseDown)
  {
    cTheta += (float) (xpos - lastX) * cameraRotateSpeed;
    cPhi -= (float) (ypos - lastY) * cameraRotateSpeed;
  }

  lastX = xpos;
  lastY = ypos;
}
```


## Camera Movement

If we adjust the position of the camera in the key callback, the camera will move in small sudden jumps.
To get smooth movement, we need to save the state of each key and move the camera constantly in the render loop.

```cpp
bool moveForward = false;
bool moveBack = false;
bool moveLeft = false;
bool moveRight = false;
glm::vec3 cameraPos;
float cameraMoveSpeed = 0.1f;

void keyCallback(GLFWwindow *window, int key, int scancode, int action, int mods)
{
  // ...

  switch (key)
  {
  case GLFW_KEY_W:
    moveForward = (action != GLFW_RELEASE);
    break;
  case GLFW_KEY_S:
    moveBack = (action != GLFW_RELEASE);
    break;
  case GLFW_KEY_A:
    moveLeft = (action != GLFW_RELEASE);
    break;
  case GLFW_KEY_D:
    moveRight = (action != GLFW_RELEASE);
    break;
  }
}

void render()
{
  // ...

  glm::vec3 up = glm::vec3(0, 1, 0);
  glm::vec3 forward = glm::vec3(cos(cTheta) * cos(cPhi), sin(cPhi), sin(cTheta) * cos(cPhi));
  glm::vec3 right = glm::cross(forward, up);

  if (moveForward)
    cameraPos += forward * cameraMoveSpeed;
  if (moveBack)
    cameraPos -= forward * cameraMoveSpeed;
  if (moveLeft)
    cameraPos -= right * cameraMoveSpeed;
  if (moveRight)
    cameraPos += right * cameraMoveSpeed;

  // ...
}
```
