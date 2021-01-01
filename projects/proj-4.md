---
layout: post
title: 'Catch a Moving Target'
---

In this programming assignment, I implemented the <font color = "black"><b>A* Search Algorithm</b></font> to allow a point robot to catch a moving object. During execution, the planner was given an 8-connected 2D gridworld (that is, the robot can only move by at most one unit along the X and/or Y axis). Each cell in the gridworld was associated with the cost of moving through it. This cost was a positive
integer. For each map, there is an associated collision threshold specified for the planner. Any cell with cost greater than this threshold was considered an obstacle that the robot could not traverse. The gridworld was of size M by N, with the bigger of two gridworlds in this assignment 1,825 x 2,332 units. 

The robot has complete knowledge of the target trajectory a priori and has to plan a path quickly. It was expected to catch the target before its trajectory ended while also incurring the lowest possible cost during the pursuit. The planner was tested on 4 maps, with a different target trajectory in each. <font color = "black"><b>The robot's trajectory is shown in green while the target's trajectory is shown in magenta</b></font>. The A* Search Algorithm I implemented allowed the robot to catch the target on all 4 maps provided. The overlaid trajectories are shown in the figures below.

<font color = "black"><b><p style="color:black;font-size:22px;">Map 1</p></b></font>
<P>Overlaid robot and target trajectories:</P>
<center><img src="/assets/img/projects/proj-4/map1.jpg" alt="map1" class="center" width="500" height="450"></center>

<font color = "black"><b><p style="color:black;font-size:22px;">Map 2</p></b></font>
<P>Overlaid robot and target trajectories:</P>
<center><img src="/assets/img/projects/proj-4/map2.jpg" alt="map2" class="center" width="500" height="450"></center>

<font color = "black"><b><p style="color:black;font-size:22px;">Map 3</p></b></font>
<P>Overlaid robot and target trajectories:</P>
<center><img src="/assets/img/projects/proj-4/map3.jpg" alt="map3" class="center" width="500" height="450"></center>

<font color = "black"><b><p style="color:black;font-size:22px;">Map 4</p></b></font>
<P>Overlaid robot and target trajectories:</P>
<center><img src="/assets/img/projects/proj-4/map4.JPG" alt="map4" class="center" width="500" height="450"></center>


