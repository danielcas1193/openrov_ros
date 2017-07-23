# OpenROV Teleooperatoin Node

## General info
This package is a fork of the package written by David Lane and Connor Brew, and build upon their initial work to allow teleoperation of the OpenROV via ROS. The teleop node here utilizes a forked version of the OpenROV ROS cockpit plugin ([origional details here](https://forum.openrov.com/t/ros-integration-via-roslibjs/2659)).

Currently, the teleopteration node can control the following aspects of the ROV:
+ Thrusters
+ Lights
+ Lasers
+ Camera Tilt

And the following OpenROV telemetry values are published as ROS topics:
+ Navdata (existing)
+ ROV Status (existing)
+ Light Level
+ Laser Status
+ BBB CPU load
+ Battery voltage
+ Battery current
+ OpenROV cape current
+ Camera Servo tilt

The thruster commands were written in a way such that custom thrust mappings can easily be implemented (e.g. use a thrust curve generated by imperical measurement). There is much room for improvement in the thrust area alone (real thrust mappings,

Control stick gains (sensitivity), and joystick configuration can be set in the teleop.launch file.

This was tested and built under ROS Indigo & Ubuntu 14.04.

install ros indigo...http://wiki.ros.org/indigo/Installation/Ubuntu

install rosbridge & gscam
```
sudo apt-get install ros-indigo-rosbridge-server

sudo apt-get install -y ros-indigo-rosbridge-suite gstreamer0.10 libgstreamer-plugins-base0.10-dev ros-indigo-image-transport ros-indigo-camera-calibration-parsers ros-indigo-camera-info-manager

cd ~/catkin_ws/src
git clone https://github.com/ros-drivers/gscam
cd ..
catkin_make
```

install openrov_ros in your catkin workspace
```
cd ~/catkin_src
git clone https://github.com/laughlinbarker/openrov_ros.git openrov
cd ..
catkin_make
```
