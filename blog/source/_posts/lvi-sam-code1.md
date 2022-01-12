---
title: 
date: ###
categories: slam
tags: ###
keywords: LVI-SAM
---

# LVI-SAM代码注释 
- - - -
<!--more-->
## 总体概述

***从节点关系图入手
在配置好环境之后运行roslaunch lvi_sam run.launch
之后使用rqt_graph查看节点和话题之间的连通关系
主要节点分别是/lvi_sam_imuPreintegration(IMU预积分点)/lvi_sam_mapOptmization(因子图优化节点) ,/lvi_sam_featureExtraction(激光雷达特征点提取节点) , /lvi_sam_imageProjection(生成深度图),/lvi_sam_visual_feature(生成视觉特征点),/lvi_sam_visual_loop(回环检测), /lvi_sam_visual_odometry(视觉里程计)***

1. Node:lvi_sam_imuPreintegration
![lvi_sam_imuPreintegration](imuPreintegration.jpg)
	1. 输入
	原始imu数据
	雷达里程计的信息
	```
	ros::Subscriber subImu;//在类里面定义

	ros::Subscriber subOdometry;	//在IMUPreintegration()中

	subImu = nh.subscribe<sensor_msgs::Imu> (imuTopic, 2000, &IMUPreintegration::imuHandler, this, ros::TransportHints().tcpNoDelay());

	subOdometry = nh.subscribe<nav_msgs::Odometry>(PROJECT_NAME + "/lidar/mapping/odometry", 5, &IMUPreintegration::odometryHandler, this, ros::TransportHints().tcpNoDelay());
	```
	2. 输出
	imu里程计信息
	imu的path
	```
	ros::Publisher pubImuOdometry;

	ros::Publisher pubImuPath;

	pubImuOdometry = nh.advertise<nav_msgs::Odometry> ("odometry/imu", 2000);
	pubImuPath = nh.advertise<nav_msgs::Path> (PROJECT_NAME + "/lidar/imu/path", 1);
	```
	* imu/path单纯用于rviz的显示 *
	![imu/path](/home/koy/桌面/slam-english/imu_path单纯用来显示.png)
	* /odometry/imu 作为视觉里程计的输入，辅助视觉里程计初始化 *
	![/odometry/imu](/home/koy/桌面/slam-english/imu-odometry输入给visual-odo.png)

2. Node: lvi_sam_imuPreintegration
