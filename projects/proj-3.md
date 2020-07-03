---
layout: post
title: '3D Dense Reconstruction using ICP and Point-based Fusion'
---

In this programming assignment, I implemented a basic 3D dense mapping system that
reconstructs a 3D dense model of a static indoor environment with given RGB-D image sequences. The system
follows the tracking and mapping framework proposed in [1], which is commonly used in many state-of-the-art
visual tracking and mapping systems. In this framework, mapping relies on the pose estimation from tracking to
update the global model, and tracking uses the refined global model from mapping as reference. The visual tracking
part of the system, which is also known as localization or visual odometry (VO), was solved using point-to-plane
iterative closest point (ICP) [2]. The mapping part was done using point-based fusion [1]. However, unlike in
[1], we do not consider the estimation of dynamic objects in this homework since the input data are from a static
environment. Also, for simplicity and efficiency, I implemented both ICP and point-based fusion
with some modifications from the original algorithms.

The 3D dense reconstructed indoor scene, obtained by modifying the standard ICP algorithm is shown below:
<img src="icp.png" alt="ICP">.












References:

[1] Keller, Maik, et al. “Real-time 3D reconstruction in dynamic scenes using point-based fusion.” International
Conference on 3D vision (3DV), 2013. <a href="http://ieeexplore.ieee.org/document/6599048/">Link to paper</a>.

[2] Newcombe, Richard A., et al. “KinectFusion:Real-time dense surface mapping and tracking.” 10th IEEE International Symposium on Mixed and Augmented Reality (ISMAR), 2011. <a href="http://ieeexplore.ieee.org/document/6162880/">Link to paper</a>.

[3] 