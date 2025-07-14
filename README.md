# Autonomous Navigation with LiDAR-Camera Fusion and TD3

This project demonstrates autonomous navigation using **LiDAR-Camera fusion** and the **TD3** deep reinforcement learning algorithm in a ROS and Gazebo-based simulation environment.

The system uses LiDAR-Camera fusion to perceive the environment and navigates autonomously using the **TD3** (Twin Delayed Deep Deterministic Policy Gradient) algorithm. Training takes place in a simulated environment built on **ROS Noetic** and **Gazebo 11**.

---

## Requirements

- **ROS Noetic**  
- **Gazebo 11**  
- **Ubuntu 20.04**

---

## Installation, Setup, and Training

### Step 1: Clone the repository

```bash
git clone https://github.com/Seher-789/Autonomous-navigation.git
cd ~/Autonomous-navigation/DRL-robot-navigation/catkin_ws
```
### Step 2: Compile the workspace
```bash
catkin_make_isolated
```
### Step 3: Set environment variables
```bash
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://localhost:11311
export ROS_PORT_SIM=11311
export GAZEBO_RESOURCE_PATH=~/Autonomous-navigation/DRL-robot-navigation/catkin_ws/src/multi_robot_scenario/launch
source ~/.bashrc
```
### Step 4: Source the workspace
```bash
cd ~/Autonomous-navigation/DRL-robot-navigation/catkin_ws
source devel_isolated/setup.bash
```
### Step 5: Launch the LiDAR-Camera Fusion Node
```bash
roslaunch lidar_camera_fusion vlp16OnImg.launch
```
### Step 6: Train the Agent with TD3
```bash
cd ~/Autonomous-navigation/DRL-robot-navigation/TD3
python3 train_velodyne_td3.py
```
### Step 7: Monitor Training with TensorBoard
```bash
cd ~/Autonomous-navigation/DRL-robot-navigation/TD3
tensorboard --logdir runs
```
### Notes: Kill all ROS and Gazebo processes if needed
```bash
killall -9 rosout roslaunch rosmaster gzserver nodelet robot_state_publisher gzclient python python3
```

### Project Structure
lidar_camera_fusion/ – LiDAR-camera fusion pipeline
DRL-robot-navigation/TD3/ – TD3 training scripts and environments
catkin_ws/ – ROS workspace for simulation

### Reference Paper
Seher and R. A. Wagan,
"Twin Delayed Deep Deterministic Policy Gradient for Adaptive Autonomous Navigation with LiDAR and Camera Sensor Fusion in Diverse Environment,"
2025 International Conference on Communication Technologies (ComTech), Rawalpindi, Pakistan, 2025, pp. 1-6,
doi: 10.1109/ComTech65062.2025.11034457.

