# Universal-Robot-simulation-using-ROS2-RViz

## Summary
Simple Universal Robot simulation in ROS2 and connecting to a real UR10.

## Requirements
Ubuntu Noble 24.04,
ROS 2 Jazzy Desktop

## ROS 2 packages
colcon-common-extensions,
ur_robot_driver

## Installation
ROS 2 was installed using the official documentation.

https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html

After sourcing the environment, necessary packages were installed.

```bash
sudo apt update
sudo apt install python3-colcon-common-extensions
sudo apt install ros-jazzy-ur
```
## Simulation
For a simple simulation, ur_robot_driver package had all the necessary scripts.
Simulation was done by using ur_robot_driver mock hardware and Moveit2 MotionPlanning panel in RViz2.

Terminal 1
```bash
ros2 launch ur_robot_driver ur_control.launch.py ur_type:=ur10 robot_ip:=0.0.0.0 use_mock_hardware:=true
```
Terminal 2
```bash
ros2 launch ur_moveit_config ur_moveit_launch.py ur_type:=ur10 launch_rviz:=true
```


<img width="1752" height="903" alt="Simulation" src="https://github.com/user-attachments/assets/a756c313-ccaf-481e-966e-2f6601ba6539" />

From the MotionPlanning panel the robot can be controlled by moving the goal state of the robot and the commanding to plan and execute the movement. The simulated robot can be seen on the right window.


<img width="499" height="280" alt="Query States" src="https://github.com/user-attachments/assets/65055e1a-a56b-42bf-86ff-97b7c6ab3d79" />

The start state and goal state visibility can be toggled under Planning Request tab.


<img width="500" height="352" alt="Joints" src="https://github.com/user-attachments/assets/671096b8-19ca-4bf5-bed4-9203c9cdb91f" />

The states could be moved by adjusting the joint angles or by moving the ball at Tool Center Point.


## Connecting to a real UR10
In order to connect the robot with ROS2, External Control URCap needed to be set up according to universal robot documents. 

https://docs.universal-robots.com/Universal_Robots_ROS2_Documentation/doc/ur_client_library/doc/setup/robot_setup.html

The ROS2 machine was assigned with a static ip in the same subnet. Devices were the connected to the same network.

Launching the ROS2 was the same as in the simulation but with real robot ip and no mock hardware. The UR10 connected succesfully and the position of the robot could be seen at in the RViz2 window. 
However when trying to execute a movement from the MotionPlanning panel it failed.




