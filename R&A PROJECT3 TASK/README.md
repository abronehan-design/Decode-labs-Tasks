# Project 3 - Autonomous Mobile Robot (AMR) Navigation

## Overview

This project simulates an autonomous mobile robot navigating a maze using LiDAR-based mapping and A* path planning. The robot builds its own map, plans a path to the goal, and replans when a dynamic obstacle blocks its route.

## Project Structure

```text
project3/
├── README.md
├── requirements.txt
├── maze_environment.py
├── lidar_simulator.py
├── astar_pathfinder.py
├── robot_navigation_sim.py
└── output/
    └── navigation_result.png
```

## Implementation

### LiDAR Mapping

`lidar_simulator.py` simulates a 360° LiDAR sensor that scans the environment and updates a 2D occupancy grid. The robot only uses this generated map for navigation.

### Path Planning

`astar_pathfinder.py` implements the A* algorithm to find the shortest path from the start to the goal using the occupancy grid.

### Dynamic Obstacle Avoidance

During navigation, the robot continuously scans its surroundings. If a new obstacle blocks the planned path, it automatically computes a new route and continues toward the goal.

## Running the Project

```bash
pip install numpy matplotlib

python robot_navigation_sim.py
```

The generated visualization is saved in:

```text
output/navigation_result.png
```

## Configuration

| File                      | Description                                             |
| ------------------------- | ------------------------------------------------------- |
| `maze_environment.py`     | Maze layout, start/goal positions, and dynamic obstacle |
| `lidar_simulator.py`      | LiDAR simulation and occupancy grid generation          |
| `astar_pathfinder.py`     | A* path planning algorithm                              |
| `robot_navigation_sim.py` | Main navigation and replanning loop                     |

## Output

* Robot-generated occupancy grid
* Planned navigation path
* Dynamic obstacle detection and replanning
* Navigation visualization saved in `output/`

## Deliverables

* `maze_environment.py`
* `lidar_simulator.py`
* `astar_pathfinder.py`
* `robot_navigation_sim.py`
* `output/navigation_result.png`
* Console output showing the replanning event
