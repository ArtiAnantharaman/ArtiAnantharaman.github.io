---
layout: post
title: 'Path Planning on Constraint Manifolds'
---

In this programming assignment, I implemented the <font color = "black"><b>Rapidly-exploring Random Trees (RRT)</b></font> path planner for the Franka robot. I also implemented planning with constraints using Projection Sampling.

I coded the RRT algorithm to move the robot arm from initial position to target position with collision avoidance, the video for which is below <font color = "black"><b>(unconstrained planning)</b></font>:
<iframe width="560" height="315" src="https://www.youtube.com/embed/n3T3_oE5H1s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> 


It is noticeable in the video above that the end-effector of the robot undergoes significant rotations. This may not be desirable in real-world scenarios; for example, if the robot is grasping an object, we may wish the object to remain upright. Hence I improved the existing planner to include <font color = "black"><b>constrained planning</b></font> via constraint projections to keep the end-effector in the vertical orientation. I incorporated gradient descent to project a given joint configuration towards the constraint manifold until a certain threshold was reached. There was some non-trivial effort in tuning hyperparameters such as the constraint threshold and the gradient step size in order to optimize the planning process.

A video of the Franka reaching the target position with its end-effector in the vertical configuration is below <font color = "black"><b>(constrained planning)</b></font>:
<iframe width="560" height="315" src="https://www.youtube.com/embed/vSM379GZVJw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>