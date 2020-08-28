---
layout: post
title: '3D Dense Reconstruction using ICP and Point-based Fusion'
---

In this programming assignment, I implemented a basic <font color = "black"><b>3D dense mapping system</b></font> that
reconstructs a 3D dense model of a static indoor environment with given RGB-D image sequences. The system
follows the tracking and mapping framework proposed in [1], which is commonly used in many state-of-the-art
visual tracking and mapping systems. In this framework, mapping relies on the pose estimation from tracking to
update the global model, and tracking uses the refined global model from mapping as reference. The visual tracking
part of the system, which is also known as localization or visual odometry (VO), was solved using point-to-plane
iterative closest point (ICP) [2]. The mapping part was done using point-based fusion [1]. However, unlike in
[1], we do not consider the estimation of dynamic objects in this homework since the input data are from a static
environment. Also, for simplicity and efficiency, I implemented both ICP and point-based fusion
with some modifications from the original algorithms.

<P>The 3D dense reconstructed indoor scene, obtained by modifying the standard ICP algorithm [2] is shown below:</P>
<img src="/assets/img/projects/proj-4/icp.png" alt="ICP">.

The <font color = "black"><b>point-to-plane ICP</b></font>[1] performs well and results in a good reconstruction. The registration of successive frames into a global model is good and yields a reasonably well-structured output. Objects like the paintings on the wall have a “wavey” shape
to them, quite unlike paintings in the real-world. The outlines of objects like the painting frames, cushions, etc. are not as sharp as one would expect, though overall, the semantic information conveyed in the reconstructed scene in quite good. However,
the trajectory shown in red has a big discontinuity towards the end and seems to break off towards the end position. The likely reason for the suboptimal performance could be the fact that this modified ICP only iterates on one downsampled level with few iterations.

An improved reconstruction is obtained using <font color = "black"><b>point-based fusion</b></font>. Volumetric fusion methods have high computational overheads [3] owing to continuous transitions between different data representations. Using regular voxel grids imposes memory overheads because both empty space and surfaces are represented densely [3], limiting the size of the reconstruction volume. On the other hand, point-based fusion methods lower the memory overhead associated with volumetric approaches and can therefore be employed in large-scale reconstructions.

<P>The 3D dense reconstructed indoor scene, obtained by incorporating point-based fusion [1] is shown below:</P>
<img src="/assets/img/projects/proj-4/pf.png" alt="pf">.


The point-based fusion seems to perform much better than ICP in reconstructing the scene. The paintings on the wall have frames that are rectangular and the opposite edges of the frames are parallel to each other, as one would expect. The contours of the red, blue, and green cushions are also sharp and clearly demarcated from the background. The trajectory shown in red is also continuous and
well-formed across all the frames. So we can certainly say point-based fusion outperforms the plain ICP approach.

Using the fusion model as the next reference frame results in better ICP registration than using current frame as the next reference frame. The reason is that in pure ICP approaches, we simply “merge” the incoming frame with the global model
using the 'R' and 't' that ICP computes. We do not seek to make sense of and associate different instances of a given object across all frames to yield a cohesive reconstruction of the object within the scene. In contrast, point-based fusion has a sophisticated data association strategy that yields well-formed reconstructions. By projecting the global model onto the image plane and
using a confidence count metric to pick correspondences, all the points that represent the same object are “fused” over time, preserving its geometric properties. The directions of the normals of close-enough points are compared to make sure that they are
pointing in the same direction before fusing the corresponding points, which further improves the geometric properties of the reconstruction.




<font color = "black"><b>References:</b></font>

[1] Keller, Maik, et al. “Real-time 3D reconstruction in dynamic scenes using point-based fusion.” International
Conference on 3D vision (3DV), 2013. <a href="http://ieeexplore.ieee.org/document/6599048/">Link to paper</a>.

[2] Newcombe, Richard A., et al. “KinectFusion:Real-time dense surface mapping and tracking.” 10th IEEE International Symposium on Mixed and Augmented Reality (ISMAR), 2011. <a href="http://ieeexplore.ieee.org/document/6162880/">Link to paper</a>.

[3] Handa, Ankur, et al. “A benchmark for RGB-D visual odometry, 3D reconstruction and SLAM." IEEE International Conference on Robotics and Automation (ICRA), 2014. <a href="https://www.doc.ic.ac.uk/~ahanda/VaFRIC/iclnuim.html">Website</a>.
