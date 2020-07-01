# A example of SLAM in ROS

## Overview

This project describes how to simulate a simple SLAM process in ROS. Here, a robot follow a predetermined path to get out of a room.
The robot makes use of laser scan to identify the walls.

![SLAM in ROS](/slam_basic/rvi2.png "rvi2")

SLAM, the acronym for Simultaneous Localization and Mapping, is a thecnique used by robots and autonomous cars to build a map of an 
environment at the same time that locate itself. In ROS we can do this through **RVIZ**, a tool that helps you to see what's going on.

This project is just one of the firsts steps into the ROS world.

## Files

### Robot

The robot is a simple parallelepiped with 3 wheels. It also has a plugin to the hokuyo laser scan, for the SLAM. The primeiro_bot.urdf 
is the file that describes this bot.

### Launch

In the launch file the rviz, the gazebo, the world, all the nodes are initialized and the robot is placed in the world. 
The file that make thhis is bot_model.launch.

### World

The world is the stage on which the simulation operates. It is loaded in gazebo. In this case, the world loads a ground and a structure
that is formed by 4 walls with a little gap, that's where the robot pass.

![Gazebo World](/slam_basic/gazebo_model.png "gazebo_model")

### Config

The files in this folder loads the basic parameters for the SLAM in rviz.

### Nodes

ROS work with nodes.The most important are the /scan node, that gets the value from the laser scaner, the /gmapping, that maps the place,
the /odom, that get the values of the pose, position and orientation, of the robot. The nodes are describes below.

![Gazebo World](/slam_basic/rqt_graph.png "rqt_graph")

## Dependencies

  - ROS Melodic
  - Catkin
  - Rviz
  - Gazebo
  
## To build

You must follow in terminal:

- Create the catkin workspace:

```sh
$ mkdir catkin_ws
$ cd catkin_ws
$ mkdir src
$ catkin_make
```

- Cloning the repository and building:

```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/marcos-moura97/slam_basic_ros.git
$ cd ..
$ catkin_make
```

## To Run

To run the project and see the gazebo world and the rviz, execute the following steps:



- Running roscore

```sh
$ cd ~/catkin_ws/
$ source devel/setup.bash
$ roscore
```

- Launching the program

```sh
$ roslaunch bot_model.launch
```

In the RVIZ, select some nodes, as the image below shows, and add a path to follow with the tool **2D Nav Goal** pointing to the place
that you want to follow.

![SLAM in ROS](/slam_basic/rviz1.png "rviz1")

## Final message

I hope this helps you to enjoy robotics as much as I do :)

