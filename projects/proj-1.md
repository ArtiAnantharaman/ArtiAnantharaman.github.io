---
layout: post
title: 'Augmented Reality for Minimally Invasive Surgery'
---
This is my <b>Capstone Project</b> as part of my Master's in Robotic Systems Development (MRSD) at Carnegie Mellon. My team and I are advised by Dr. Howie Choset at the Biorobotics Lab in CMU.

The <font color = "black"><b>Chopsticks Robotic Surgical System</b></font> is a product that can overcome the limitations of conventional tumor localization. In typical tumor resection procedures, a surgeon has to make a large incision to gain access to the diseased organ and will manually palpate the organ to locate embedded tumors. Regions of abnormally high stiffness in the organ indicate the presence of tumors. The patient will have to be hospitalized for longer and is at a higher risk of infection because of the large incision needed for the non-laparoscopic surgery. In addition to this method prolonging the hospitalization time of the patient, supplementary preoperative images such as CT scans make the procedure very expensive. It is also cognitively demanding for the surgeon who must form a correspondence between these tumor positions with the CT scans. CT scans are also expensive in the United States, with an average cost of $3,275.

The Chopsticks surgical system built on top of the <font color = "black"><b>da Vinci Research Kit (dVRK)</b></font> circumvents the need for preoperative images of the organ by constructing a 3D organ model in real-time while accounting for the natural movements of the organ. The robot palpates the organ to search for tumors and overlays their location and shape onto the visual feed for the surgeon to see in real-time. This system helps the surgeon perform an easier surgery as well as contributing to lower patient costs and healing times.

The video below demonstrates the work done so far on the surgical system:

<iframe width="560" height="315" src="https://www.youtube.com/embed/tUwB2kyOg7o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The system's functional requirements, cyberphysical architecture, CAD drawings, timeline, etc. can be found on the <a href="https://mrsdprojects.ri.cmu.edu/2020teama/">project website</a>.

<font color = "black"><b>My contributions to the development of the surgical system so far are:</b></font>
1. Registered robot and stereo camera coordinate frames with a root-mean-squared error of 4 mm using Horn's method
2. Registered laser scanner and robot coordinate frames with a 5.348 pixel unit reprojection error
3. Wrote control code to have the dVRK scan phantom organ in under 5 minutes to generate a 3D point cloud
4. Registered point cloud of liver to ground truth CAD model with a root-mean-square error of 2 mm using ICP (on CloudCompare software)
5. Wrote code to estimate frequency of motion of liver using Principal Component Analysis and Fast Fourier Transform with a 0.05 Hz margin of error

The goal for Fall 2020 is to incorporate motion compensation techniques to 3D-scan and palpate a moving liver. The localized tumors will be overlaid on the surgeon's visual feed using augmented reality.



