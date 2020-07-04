---
layout: post
title: 'Spatial Kinematics of a 7-DoF Robotic Arm'
---

In this programming assignment, I calculated the forward and inverse kinematics of the 7-DoF robot arm using which I implemented a box-box collision checking scheme.

The <font color = "black"><b>forward kinematics</b></font> of the Franka Panda robot were computed from the Denavit-Hartenberg parameters provided by the robot manufacturer. The <font color = "black"><b>inverse kinematics</b></font> of the arm were computed using the <font color = "black"><b>Jacobian Transpose Method</b></font>, for which this <a href="https://homes.cs.washington.edu/~todorov/courses/cseP590/06_JacobianMethods.pdf">link</a> proved to be very helpful.

In order to implement a collion checker, the links of the robot arm were modelled as <font color = "black"><b>oriented bounding boxes (OBB)</b></font>. The <font color = "black"><b>Separating Axis Theorem (SAT)</b></font> was applied to determine if the arm was in collision with a user-controlled object in 3D space. SAT states that: “If two convex objects are not intersecting, there exists an axis for which the projection of the objects will not overlap.” This <a href="https://www.jkh.me/files/tutorials/Separating%20Axis%20Theorem%20for%20Oriented%20Bounding%20Boxes.pdf">link</a> provides significant insight into the SAT. 

The video below depicts the collion checking scheme. The cube is moved around and the light turns red when the cube is in collision with the robot.
<iframe width="560" height="315" src="https://www.youtube.com/embed/z1sWPv5JMVs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

My foothold of robot controls and manipulations was strengthened in doing this project, and I absolutely enjoyed watching my code manifest into a real-time collion checker that could have diverse real-world applications!