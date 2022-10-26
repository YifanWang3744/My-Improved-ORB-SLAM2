# My-Improved-ORB-SLAM2

An improved ORB-SLAM2 system which fixes the problem of the locating failure of ORB-SLAM2 system running on some data sets. 

## ORB-SLAM2

ORB-SLAM2 is a real-time SLAM library for **Monocular**, **Stereo** and **RGB-D** cameras that computes the camera trajectory and a sparse 3D reconstruction (in the stereo and RGB-D case with true scale). It is able to detect loops and relocalize the camera in real time. We provide examples to run the SLAM system in the [KITTI dataset](http://www.cvlibs.net/datasets/kitti/eval_odometry.php) as stereo or monocular, in the [TUM dataset](http://vision.in.tum.de/data/datasets/rgbd-dataset) as RGB-D or monocular, and in the [EuRoC dataset](http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) as stereo or monocular. We also provide a ROS node to process live monocular, stereo or RGB-D streams. **The library can be compiled without ROS**. ORB-SLAM2 provides a GUI to change between a *SLAM Mode* and *Localization Mode*, see section 9 of this document.

<a href="https://www.youtube.com/embed/ufvPS5wJAx0" target="_blank"><img src="http://img.youtube.com/vi/ufvPS5wJAx0/0.jpg" 
alt="ORB-SLAM2" width="240" height="180" border="10" /></a>
<a href="https://www.youtube.com/embed/T-9PYCKhDLM" target="_blank"><img src="http://img.youtube.com/vi/T-9PYCKhDLM/0.jpg" 
alt="ORB-SLAM2" width="240" height="180" border="10" /></a>
<a href="https://www.youtube.com/embed/kPwy8yA4CKM" target="_blank"><img src="http://img.youtube.com/vi/kPwy8yA4CKM/0.jpg" 
alt="ORB-SLAM2" width="240" height="180" border="10" /></a>

## Description

In some datasets, for example, [EuRoC](https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets) v203 set, when the cameera moves quickly, the common feature points between the previous and current frames would be less than the threshold, leading to localization failure. 

To solve this problem, I developed an improved ORB-SLAM2 system based on **image pyramid**. In the tracking and locating part, an alternative method was used for localization when the motion model locating method failed. First, **scaling** was performed by building an image pyramid, **matching feature points** at different scales from the bottom to the top, and then **roughly locating** according to the **relative position** of the current frame and the previous frame, and finally **adjusting and optimizing** the pose through the feature points. 

After testing, the accuracy of the improved system has been **improved by 5%**, while the real-time performance has hardly changed. From the trajectory graph, it could also be intuitively observed that the simulated trajectory of the improved system was more closely aligned with the actual motion trajectory.

## Result
<p align="center">
  <img src="https://user-images.githubusercontent.com/93358121/162555344-110bc303-47d3-4f42-9e59-2172d8ec08f5.png" />
  <img src="https://user-images.githubusercontent.com/93358121/162555349-252433f2-91f6-41ca-882f-403cffcd3f5e.png" />
  <img src="https://user-images.githubusercontent.com/93358121/162555353-be0d22c0-6c5b-4ac1-96d3-b005875f0c7f.png" />
</p>
