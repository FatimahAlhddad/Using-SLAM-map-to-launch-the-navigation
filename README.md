# Using-SLAM-map-to-launch-the-navigation
This repository shows the steps taken to launch the navigation by using the SLAM map.

###### Requirements:
1. Ubuntu version 18.04
2. ROS melodic installation 
3. map has to be prepared before running the Navigation

## (1) Launch Simulation World:
```
$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

## (2) Run Navigation Node:
Open a new terminal and run the Navigation node.
```
$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```

in step (2) I face an error I solved by using this command:

`$ sudo apt-get install ros-melodic-dwa-local-planner`

## (3) Estimate Initial Pose:
1. Click the 2D Pose Estimate button in the RViz menu.
2. Click on the map where the actual robot is located and drag the large green arrow toward the direction where the robot is facing.
3. Repeat step 1 and 2 until the LDS sensor data is overlayed on the saved map.
4. Launch keyboard teleoperation node to precisely locate the robot on the map.

`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`

5. Move the robot back and forth a bit to collect the surrounding environment information and narrow down the estimated location of the TurtleBot3 on the map which is displayed with tiny green arrows.


![image](https://user-images.githubusercontent.com/85858256/124842470-43c5ed80-df98-11eb-986f-e07db99ed4b3.png)

![image](https://user-images.githubusercontent.com/85858256/124842546-75d74f80-df98-11eb-9d0e-21924163f603.png)

6. Terminate the keyboard teleoperation node by entering Ctrl + C




## (4) Set Navigation Goal
1. Click the 2D Nav Goal button in the RViz menu.
2. Click on the map to set the destination of the robot and drag the green arrow toward the direction where the robot will be facing.

## The Result:

![image](https://user-images.githubusercontent.com/85858256/124843017-a8ce1300-df99-11eb-89e5-9664e0276a4f.png)


