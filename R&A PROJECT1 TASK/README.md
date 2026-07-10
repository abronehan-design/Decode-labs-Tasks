# Project 1 - Robotic Arm Kinematics & Path Planning

## Overview

This project simulates a 6-DOF robotic arm that moves its end-effector from Point A to Point B using Inverse Kinematics (IK). A smooth trajectory is generated while avoiding obstacles in the workspace.

## Project Structure

```text
project1/
├── README.md
├── requirements.txt
├── forward_kinematics.py
├── inverse_kinematics.py
├── trajectory_planner.py
├── robotic_arm_sim.py
└── output/
    └── arm_trajectory_result.png
```

## Implementation

### Input

The robotic arm is modeled using Denavit-Hartenberg (DH) parameters. The simulation takes a start position, target position, and an obstacle.

### Processing

#### Forward Kinematics (`forward_kinematics.py`)

Computes the end-effector position from the given joint angles using DH transformation matrices.

#### Inverse Kinematics (`inverse_kinematics.py`)

Uses a Damped Least Squares (DLS) solver to compute joint angles while handling singularities and enforcing joint limits.

#### Trajectory Planning (`trajectory_planner.py`)

Generates a smooth quintic trajectory between the start and target positions. If the direct path intersects the obstacle, the planner automatically creates a collision-free path through an intermediate waypoint before solving IK for each waypoint.

### Output

The simulation produces:

* Joint angles for each waypoint
* Final end-effector position error
* A 3D visualization of the robotic arm, obstacle, and planned trajectory

## Running the Project

```bash
pip install numpy matplotlib
python robotic_arm_sim.py
```

The output image is saved as:

```text
output/arm_trajectory_result.png
```

## Configuration

| File                    | Description                                       |
| ----------------------- | ------------------------------------------------- |
| `robotic_arm_sim.py`    | Start/end positions and obstacle configuration    |
| `forward_kinematics.py` | DH parameters and joint limits                    |
| `inverse_kinematics.py` | Damping factor, tolerance, and maximum iterations |
| `trajectory_planner.py` | Number of waypoints and collision clearance       |

## ROS 2 Mapping

| Project Module           | ROS 2 Equivalent                   |
| ------------------------ | ---------------------------------- |
| `forward_kinematics.py`  | `robot_state_publisher` + TF2      |
| `inverse_kinematics.py`  | MoveIt IK Plugins                  |
| `trajectory_planner.py`  | MoveIt Planning Scene + FCL        |
| `robotic_arm_sim.py`     | `FollowJointTrajectory` Controller |
| Matplotlib Visualization | RViz / Gazebo                      |

## Deliverables

* Source code (`.py` files)
* `output/arm_trajectory_result.png`
* Console output demonstrating obstacle detection and path replanning
* Short explanation of how the project can be extended to full pose (position and orientation) control using ROS 2 and MoveIt
