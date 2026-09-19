# Week 2


**Goal this week:** Formally present the Watchwing project to the group and finalize the technical direction.

## What we did


This week, we formally presented the **Watchwing project** to the group. We explained the main goals of the project, its scope, and the overall architecture that we were planning to use. We also presented the concept of the autonomous UAV, which is a fixed-wing drone designed to fly through a predefined route using a set of GPS waypoints.

We explained how the main **change-detection system** would work. The UAV will first fly through a fixed route containing a number of GPS waypoints, for example, five points. At each waypoint, the camera will be triggered using GPS to capture an image. We called this first set of images **Round A**. After some time, the UAV will fly the same route again and capture images at the same five waypoints, which we called **Round B**. The images from both flights will then be compared with each other, such as Point 1 from Round A with Point 1 from Round B, Point 2 with Point 2, and so on. If a significant difference is found between two corresponding images, that area can be flagged as a possible change.

We also discussed the different components that would be required to make the system work. The planned system would use a **Pixhawk flight controller** running **ArduPilot's ArduPlane firmware**, along with GPS and IMU sensors for navigation and orientation. We planned to use **Mission Planner** as the ground-control software, with **MAVLink** being used for communication between the ground station and the UAV.

During the discussion, we also decided to record a **continuous video throughout the entire flight**. This video would be saved onto an onboard SD card so that the complete flight could be manually inspected later if required. This would give us an additional source of information apart from the individual images captured at the waypoints.

However, while discussing the system in more detail, we came across a few problems that needed to be solved. We were still unsure about which specific flight controller hardware would be the most suitable for our UAV. Another important problem was figuring out how accurately the UAV could return to the exact same position and orientation at each waypoint during different flights. Since our change-detection method depends on comparing images taken from the same locations, even a small difference in the position or orientation of the UAV could affect the accuracy of the image comparison.

After discussing these issues, we finalized the basic approach for the change-detection system. We decided to use **GPS-triggered images captured at fixed waypoints** and compare the corresponding images from different flight rounds. Along with this, we would maintain a continuous video recording of the flight on the onboard SD card for manual inspection. With the basic technical direction decided, we were ready to move on to the physical construction of the UAV.

## Problems and blockers


One of the main problems we faced this week was deciding between the different **flight controller hardware options**. We also needed to understand how accurately the UAV could return to the same position and maintain the same orientation at each waypoint during repeated flights. This is important because the images captured during different rounds need to be sufficiently similar in terms of viewpoint for the change-detection system to work reliably.

## Decisions


We decided to use a **GPS-triggered image capture system**, where the UAV captures images at predefined waypoints during each flight. The images from different rounds will then be compared point-to-point to identify possible changes in the monitored area. We also decided to record a **continuous video of the entire flight** and store it on the onboard SD card so that the flight can be manually reviewed whenever necessary.

## Next week
Start with the body of UAV

Next week, we will start working on the **body of the UAV**. We will begin developing the physical airframe of the fixed-wing aircraft and work on the initial design and construction.
