---
layout: post
title: 'Object Tracking'
---

In computer vision, the <font color = "black"><b>Lucas–Kanade optical flow algorithm</b></font> is a widely used differential method for optical flow estimation developed by Bruce D. Lucas and Takeo Kanade. It assumes that the flow is essentially constant in a local neighbourhood of the pixel under consideration, and solves the basic optical flow equations for all the pixels in that neighbourhood, by the least squares criterion. Lucas-Kanade  optical flow algorithm is a simple technique which can provide an estimate of the movement of interesting features in successive images of a scene. We would like to associate a movement vector (u,v) to every such ”interesting” pixel in the scene, obtained by comparing the two consecutive images.

The Lucas-Kanade algorithm makes some <font color = "black"><b>implicit assumptions:</b></font>

– The two images are separated by a small time increment ∆t, in such a
way that objects have not displaced significantly (that is, the algorithm
works best with slow moving objects).

– The images depict a natural scene containing textured objects exhibiting shades of gray (different intensity levels) which change smoothly.

The algorithm does not use color information in an explicit way.  It does not scan  the  second  image  looking  for  a  match  for  a  given  pixel.   It  works  by trying to guess in which direction an object has moved so that local changes in intensity can be explained.

Helpful links to understand the Lucas-Kanade algorithm:
1. <a href="https://www.ri.cmu.edu/pub_files/pub3/baker_simon_2002_3/baker_simon_2002_3.pdf">Lucas-Kanade 20 Years On: A Unifying Framework: Part 1</a>
2. <a href="http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.12.3095&rep=rep1&type=pdf">Lucas-Kanade 20 Years On: A Unifying Framework: Part 2</a>
3. <a href="http://www.inf.fu-berlin.de/inst/ag-ki/rojas_home/documents/tutorials/Lucas-Kanade2.pdf">Lucas-Kanade in a Nutshell</a>

The tracking of a car using the Lucas-Kanade method is shown in the video below:
<iframe width="560" height="315" src="https://www.youtube.com/embed/KOIOgSs7Res" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

It is apparent on the video above that the image content we are tracking in the first frame differs from the one in the last frame. This is understandable since we are updating the template after processing each frame and the error can be accumulating. This problem is known as <font color = "black"><b>template drifting</b></font>. To mitigate this problem, I followed the approach listed in  <a href="https://www.ri.cmu.edu/publications/the-template-update-problem//">Iain Matthews et al., 2003.</a>.

The tracking of a car after incorporating <font color = "black"><b>template correction</b></font> is shown in the video below:
<iframe width="560" height="315" src="https://www.youtube.com/embed/Vb8oHi7OCEE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>