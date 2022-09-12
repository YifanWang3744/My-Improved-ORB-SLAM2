# My-Improved-ORB-SLAM2

## Description
In this project, I developed an improved ORB-SLAM2 system which fixes the problem of the locating failure of ORB-SLAM2 system running on some data sets. In some dataset, for example, EUROC v203 set, when the cameara moves quickly, the common feature points between the previous and current frames would be less than the threshold, leading to locallization failure. To solve this problem, I developed an improved ORB-SLAM2 system based on image pyramid. In the tracking and locating part, an alternative method is used for localization when the motion model locating method fails. First, scaling is performed by building an image pyramid, matche feature points at different scales from the bottom to the top, and then roughly locate according to the relative position of the current frame and the previous frame, and finally adjusting and optimizing the pose through the feature points. After testing, the accuracy of the improved system has been improved by 5%, while the real-time performance has hardly changed. From the trajectory graph, it can also be intuitively observed that the simulated trajectory of the improved system is more closely aligned with the actual motion trajectory.

## Result
<p align="center">
  <img src="https://user-images.githubusercontent.com/93358121/162555344-110bc303-47d3-4f42-9e59-2172d8ec08f5.png" />
  <img src="https://user-images.githubusercontent.com/93358121/162555349-252433f2-91f6-41ca-882f-403cffcd3f5e.png" />
  <img src="https://user-images.githubusercontent.com/93358121/162555353-be0d22c0-6c5b-4ac1-96d3-b005875f0c7f.png" />
</p>
