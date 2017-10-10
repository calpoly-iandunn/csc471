---
layout: assignment
assignment: "lab06"
title: Lab 6
---

<div class="alert alert-dismissible alert-danger">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <h4>Warning!</h4>
  <p>
    Base code is not yet ready for this assignment
  </p>
</div>

Today’s lab we will play with simple hierarchical modeling and the use of a matrix stack
to apply multiple transforms in a hierarchical manner.

{% include image-block.html file="lab6_1.png" alt="Lab 6 Figure 1" %}

The base code provided already draws the above figure, next:

## Step 1

Closely follow the slide presentation on hierarchical modeling and create a
complete robot chest including torso, two arms and head (each arm must include 3
pieces) and one of the arms must animate using hierarchical modeling:

**a.** The arm should include a fore arm, upper arm and hand

**b.** The fore arm should attach to the upper arm at an elbow joint

**c.** The forearm should be able to be rotated about the elbow joint

**d.** The entire robot should be able to be translated (along X is fine – link this
  movement to a keyboard event, ‘a’ to move left and ‘d’ to move right).

**e.** The entire arm should be able to be rotated about a shoulder joint in the
  upper arm.

## Step 2

You should set up the robot and the animated arm in the scene in a reasonable
position and orientation (i.e. so that it looks like a robot with arms). You will
need to demonstrate bullet points c-d. Demonstrate (c), by linking the `c` key to
adding a rotation to the elbow joint – likewise for (e) do this by controlling the
position and orientation through keyboard events or mouse events.

## Step 3

Finally add a default animation of the arm waving (i.e. have the robot wave
‘hello’) (make the motion realistic by constraining the range of angles that the
arm can move – do not make myself or the TA tell you what a wave should look
like). Trigger the animation via keyboard event ‘x’ that should allow the
animation to start and stop of the name key press.

Your robot must include hands in addition to arms such as those shown:

{% include image-block.html file="lab6_2.png" alt="Lab 6 Figure 2" %}

**Extra credit:** Feel free to be creative and add extra elements as you’d like
(a detailed hand, or torso, or the rest of the robot)
for amount of extra credit up to grader.
