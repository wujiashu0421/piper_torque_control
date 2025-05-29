# Piper Torque Controller for PAT Platform

Forked from Piper ROS (https://github.com/agilexrobotics/Piper_ros)

## 1. Changes to the original repo

### 1.1 Torque Control

Torque control is enabled by creating the **TorqueCmd** topic. For standardisation, `geometry_msgs/Vector3` is used. X = motor number, Y = Torque value, Z is unused.  Specify the joint number and reference torque, and publish.

### 1.2 Current Feedback

Motor current with timestamp is replacing the effort section in the `joint_states_single` topic.

### 1.3 Joint and positional control

Joint and positional control callback functions are deleted for safety, meaning **TORQUE CONTROL ONLY**


## 2 To use

The setup and prerequisites of this package are the same as Piper ROS, However firmware version needs to be ID'ed since there's reports on MIT not working with certain firmware versions.

Setup that worked:
**Firmware Version H-V1.2.0**
**Software Version V1.0.6**

The information is available on Piper's GUI. Firmware is attached in utils folder along with a instruction to flash (in Chinese)

The new features are introduced as followed:

### 2.2: Launching control node with torque:

`ros2 launch piper start_single_piper_torque.launch.py`

### 2.1 Send torque message

Example: To give motor #2 a 0.5 Nm of force:

` ros2 topic pub -1 /torque_cmd geometry_msgs/Vector3 "{X: 2, Y: 0.5, Z: 0}" `
