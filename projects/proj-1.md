---
layout: post
title: 'Augmented Reality for Minimally Invasive Surgery'
---
This is my <b>Capstone Project</b> as part of my Master's in Robotic Systems Development (MRSD) at Carnegie Mellon. My team and I are advised by Dr. Howie Choset at the Biorobotics Lab in CMU.

The <font color = "black"><b>Chopsticks Robotic Surgical System</b></font> is a product that can overcome the limitations of conventional tumor localization. In typical tumor resection procedures, a surgeon has to make a large incision to gain access to the diseased organ and will manually palpate the organ to locate embedded tumors. Regions of abnormally high stiffness in the organ indicate the presence of tumors. The patient will have to be hospitalized for longer and is at a higher risk of infection because of the large incision needed for the non-laparoscopic surgery. In addition to this method prolonging the hospitalization time of the patient, supplementary preoperative images such as CT scans make the procedure very expensive. It is also cognitively demanding for the surgeon who must form a correspondence between these tumor positions with the CT scans. CT scans are also expensive in the United States, with an average cost of $3,275.

The Chopsticks surgical system built on top of the <font color = "black"><b>da Vinci Research Kit (dVRK)</b></font> circumvents the need for preoperative images of the organ by constructing a 3D organ model in real-time while accounting for the natural movements of the organ. The robot palpates the organ to search for tumors and overlays their location and shape onto the visual feed for the surgeon to see in real-time. This system helps the surgeon perform an easier surgery as well as contributing to lower patient costs and healing times.


The system's functional requirements, cyberphysical architecture, CAD drawings, timeline, etc. can be found on the <a href="https://mrsdprojects.ri.cmu.edu/2020teama/">project website</a>.

The video below demonstrates the work done on hardware in <font color = "black"><b>Spring 2020</b></font>:

<iframe width="560" height="315" src="https://www.youtube.com/embed/tUwB2kyOg7o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Due to the COVID-19 pandemic, we were unable to access the robot in the Biorobotics Lab and had to switch to simulation for the remainder of the project.

The video below was recorded at the completion of the project, in <font color = "black"><b>Fall 2020</b></font>. It shows one arm of the dVRK performing the surgical procedure, start to end. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/6q6407emmPA" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Please refer to the project reports linked on our <a href="https://mrsdprojects.ri.cmu.edu/2020teama/">project website</a> to know more about our modified scope, subsystem description, and performance at the Fall Validation Demonstration.

<font color = "black"><b>My contributions to the development of the surgical system were:</b></font>
1. Registered robot and stereo camera coordinate frames with a root-mean-squared error of 4 mm using Horn's method
2. Registered laser scanner and robot coordinate frames with a 5.348 pixel unit reprojection error
3. Wrote control code to have the dVRK scan phantom organ in under 5 minutes to generate a 3D point cloud
4. Registered point cloud of liver to ground truth CAD model with a root-mean-square error of 2 mm using ICP (on CloudCompare software)
5. Wrote code to estimate frequency of motion of liver using Principal Component Analysis and Fast Fourier Transform with a 0.05 Hz margin of error
6. Implemented a resolved-rate motion controller to palpate moving liver and localize embedded tumors

I absolutely enjoyed working on this project, and had the opportunity to pick up several technical and non-technical skills over this period.



