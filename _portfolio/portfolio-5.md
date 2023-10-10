---
title: "Loosely-coupled Stereo-IMU-Wheel SLAM for Sweep Robot"
excerpt: "The framework of the program is based on [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3.git) and integrates other excellent work, such as [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion.git), [pl-slam](https://github.com/rubengooj/pl-slam.git), [Structure-SLAM-PointLine](https://github.com/yanyan-li/Structure-SLAM-PointLine.git), [gf_orb_slam2](https://github.com/ivalab/gf_orb_slam2.git) and [semidense-lines](https://github.com/shidahe/semidense-lines.git). Line features are added to deal with low-texture environments; IMU and wheel encoder are added to deal with lighting variation and motion blur; Some work of [Dr. Zhao](https://github.com/YipuZhao) is referenced for making SLAM cost-efficient.
<br/>
<img src='/images/pldark.gif' width='500'>"
collection: portfolio
---

The framework of the program is based on [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3.git) and integrates other excellent work, such as [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion.git), [pl-slam](https://github.com/rubengooj/pl-slam.git), [Structure-SLAM-PointLine](https://github.com/yanyan-li/Structure-SLAM-PointLine.git), [gf_orb_slam2](https://github.com/ivalab/gf_orb_slam2.git) and [semidense-lines](https://github.com/shidahe/semidense-lines.git). Line features are added to deal with low-texture environments; IMU and wheel encoder are added to deal with lighting variation and motion blur; Some work of [Dr. Zhao](https://github.com/YipuZhao) is referenced for making SLAM cost-efficient.

<img src='/images/sweeprobot.jpg' width='300'>

The main work is as follows,
+ VICON is used to obtain the ground truth of SLAM with an efficient pose and timestamp alignment algorithm referring to [[1]](https://igl.ethz.ch/projects/ARAP/svd_rot.pdf), [[2]](https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/20070017872.pdf), [[3]](https://furgalep.github.io/bib/furgale_iros13.pdf).
+ IMU-camera and wheel-camera calibration.
+ Referring to [pl-slam](https://github.com/rubengooj/pl-slam.git) and [Structure-SLAM-PointLine](https://github.com/yanyan-li/Structure-SLAM-PointLine.git), implement a complete visual SLAM system using both point and line features, which includes stereo matching, frame tracking, local mapping, bundle adjustment of both line feature and point feature, as well as point-line based loop detection.
+ A loosely-coupled method to fusion multi-sensor information and estimate gyro bias, referring to [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion.git).
+ ["Good feature matching"](https://arxiv.org/abs/2001.00714) and ["Local map hashing"](https://ieeexplore.ieee.org/document/8794046) are integrated.
+ Atlas map in [ORB-SLAM3](https://arxiv.org/pdf/2007.11898.pdf) is modified to let the system never be lost.
+ A semi-dense map construction algorithm, referring to [semidense-lines](https://github.com/shidahe/semidense-lines.git), was modified for stereo camera.
  <br/>
  <br/>

### Demo

SLAM visualization.
<div align=center >
    <img src="/images/ptlight.gif" width="300"/>    <img src="/images/ptdark.gif" width="300"/> 
</div>

<br/>
<div align=center >
    <img src="/images/pllight.gif" width="300"/>    <img src="/images/pldark.gif" width="300"/> 
</div>

<br/>
Map visualization.
<div align=center >
    <img src="/images/origin.png" width="210"/>  <img src="/images/semidense.png" width="200"/>  <img src="/images/grid.png" width="180"/>
</div>
<div align=center >
Left: RGB image; center: semi-dense map; right: grid map.
</div>
