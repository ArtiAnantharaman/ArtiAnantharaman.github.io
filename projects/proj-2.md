---
layout: post
title: 'Robotic Bin Picking'
---

Automated bin picking is a complex problem that is only partially solved. Automated bin picking often involves a 3D model of the parts, the robot gripper, any obstacles in the scene, sensors being used to map the bin, image analysis software, path planning software, and robot control software. A generic path planning algorithm that can handle infinite variations in part sizes and orientations is near-impossible with current technology, and weeks or months of hand-picked feature engineering often leads to unreliable performance. Companies like Covariant AI are bringing in deep reinforcement learning into the industrial manipulation space and allowing robots to learn these complex tasks via apprenticeship (by watching a human do the same task). In this project, we work on a simplified version of the same bin picking task within a photo-realistic simulator.

We followed two approaches to solving the task of automated bin picking. In the first approach, the Rapidly-exploring Random Tree (RRT) algorithm was modified to sample points from the task space of the gripper rather than from the joint configurations of the Franka Panda. This allowed us to plan in the 3D XYZ space + 4D quaternion/rotation space of the gripper. We restricted the upper and lower task space limits such that the robot arm remains in the forward half of the workspace bounds and does not perform unnatural motions. However, this implementation caused the robot to align itself horizontally with the shape to be picked up and reach a joint limit, when commanded to go to a particular shape's location. 

In order to ensure that the shapes are picked up with an upright gripper, we used the quaternion corresponding to the original pose of the Franka as the orientation throughout the forward and the reset tasks. Despite this constraint, the planner would quite often immobilize the robot if the shape was too close to the edge of the container, making it impossible to recover from such configurations.

In order to have the Franka try and grasp an object with a different plan if it failed the first time around, we added a timeout to the execution of the planned path,i.e., the waypoint would be skipped in case the time required for the environment to step to that waypoint exceeded a threshold of 0.5 seconds (set manually). This meant that waypoints that prevented the gripper from moving (possibly due to the presence of an obstacle like the container edge) would be skipped, and the Franka would jump ahead multiple waypoints in its planned path to get to a target pose. This particular workaround in our implementation boosted the robot's performance significantly.

A video of the Franka executing the task based on the RRT-with-timeout approach is below:

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=81vFBJ9JvFI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

For our second approach to this task, we decided to use images from the camera mounted on the robot's wrist. The depth map of the entire container, taken from the height that the robot was spawned at, was of poor resolution. So we used a raster scan-like approach wherein the Franka scans the container as a grid of 25 x 25 waypoints and the wrist camera captures a snapshot of the scene below at each waypoint. The center pixels of each of the 625 obtained images are concatenated to form a relatively higher resolution 25 x 25 depth map which is later thresholded using a `maximum distance' metric to the container. The objects are at a lower depth from the wrist camera compared to the base of the container and hence will be thresholded to a different value from the background. A pixel from the thresholded region is randomly sampled and the robot moves to that location and tries to grasp the shape. We try to pick the shapes up, and if any shape has been moved around or seems difficult to grasp, we start over and rescan the container.

A video of the Franka grasping shapes based on their 6 DoF pose obtained from depth images is below:

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=K5x97BLqYto" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
