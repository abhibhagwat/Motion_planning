# `Solving Motion Planning Queries for TurtleBot3 using Probabilistic Roadmap Method (PRM)`

## Pre-requisites #

Install the following software on Ubuntu 16.04:

Install Catkin, Python 2.7(code based on python 2.7 due to ROS Kinetic constraints), and Python 3 (only for verification purposes if required).
Install numpy in python environment.

Create Catkin Workspace:
Create catkin workspace and clone the pathfinder_project folder in your workspace and build it.

ROS-Kinetic:
$ cd

$ sudo apt-get update

$ sudo apt-get upgrade

$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh

$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers

TurtleBot3 libraries used:

$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git

$ git clone -b kinetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git

$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git


## Running the simulation #

To launch SLAM and PRM, use the slamprm.launch file:

$ roslaunch pathfinder slamprm.launch

	Wait for approximately 60-70 seconds for SLAM to recognize the environment and for prmplanner to generate roadmap and path. Close process using ctrl+C.

To launch the simulation for the path in Gazebo, use navigation.launch file:
$ roslaunch pathfinder navigation.launch

	The simulation starts immediately. To check the co-ordinates of the robot, you can use the following command in anothet terminal window:

$ rostopic echo /odom/pose/pose

####The simulation's completion can be checked when the robot stops at the goal point that can be seen using the above command.
Close the process using ctrl+C.

All scripts are placed under pathfinder/src/scripts.

The py_2 suffixed scripts are used in the launch file as ROS uses python 2.
To visually see the roadmap, you can run prmplanner.py in a python 3 environment with numpy installed.

Scripts description (In launch order):

1. map_generator.py: Generates mapdata.csv from rostopic occupancy grid to generate the obstacle map.

2. obs_import_py2.py: Imports the obstacle data using the above generate map data and creates prm_obstacle.csv for use in prm.

3. prmplanner_py2.py: Uses the obstacle data and creates a roadmap and also searches for the best path using A* algorithm. Returns path.csv for further use.

4. navigation.py: Provides the velocity to the robot in Gazebo to traverse the nodes obtained from path.csv. Rest of the files: Support files with functions and classes.

5. prmplanner.py: Can be used to generate visible roadmap as this uses python 3 that can run Tkinter.

6. graph.py: support file for PRM.

The path.csv file in this compressed folder is the path file for the submitted video presentation points.

## Contributors
Abhishek  Bhagwat <bhagwat@clemson.edu>

## License & copyright
© Abhishek  Bhagwat, Clemson University (CUICAR)

© Ioannis Karamouzas, Clemson University (CPSC)
