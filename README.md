# ROS-AI-Week-4-task-1

smart metods internship week 4 

# Introduction
This repository explains the process of setting up and using the TurtleBot3 robot for navigation tasks in a simulated environment using ROS Noetic. It includes instructions for installing necessary packages, configuring the TurtleBot3 model, launching the simulation in Gazebo, creating a map using SLAM, to be able to effectively control the TurtleBot3, generate a map of your environment, and navigate autonomously using the created map.

# Install TurtleBot3 packages:
    ```bash
    sudo apt install ros-noetic-turtlebot3
    sudo apt install ros-noetic-turtlebot3-simulations
    sudo apt install ros-noetic-turtlebot3-navigation
    sudo apt-get install ros-noetic-dwa-local-planner
    ```

# Set the TurtleBot3 model** (e.g., Waffle):
    ```bash
    echo "export TURTLEBOT3_MODEL=waffle" >> ~/.bashrc
    source ~/.bashrc
    ```

# Launch the TurtleBot3 world in Gazebo:
    ```bash
    roslaunch turtlebot3_gazebo turtlebot3_world.launch
    ```

# Create a Map
1. Launch the SLAM node:
    ```bash
    roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
    ```
2. Launch the teleoperation node (in a new terminal):
    ```bash
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```
3. Drive the TurtleBot around the environment: using the keyboard to create a map. Use the following keys to control the TurtleBot:
    - `w`: move forward
    - `x`: move backward
    - `a`: turn left
    - `d`: turn right
    - `s`: stop
    - `q` to stop the TurtleBot.
4. Save the map (once you are satisfied with the generated map):
    ```bash
    rosrun map_server map_saver -f ~/map
    ```
Then close the teleoperation terminal 

# Launch the navigation node:
    ```bash
    roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
    ```

# Simulation
1. Align the Robot with the Map:
   Use the 2D Pose Estimate tool in RViz to place the robot in the same position and orientation as when the map was saved.
2. Set a Navigation Goal:
   Use the 2D Nav Goal tool in RViz to set a desired position by clicking on the map. The robot will then navigate to the specified location.

   <img width="947" alt="turtlebot1" src="https://github.com/user-attachments/assets/13e90774-ddf1-4499-bdc0-4b681fb69c5a">
   <img width="950" alt="turtlebot2" src="https://github.com/user-attachments/assets/7264fd1d-6613-43fc-a510-e3c7eb31a6e4">


