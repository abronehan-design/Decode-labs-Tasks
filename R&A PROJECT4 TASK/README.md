# Project 4 - PLC-Based Conveyor Sorting System

## Overview

This project simulates the control logic of a PLC-based conveyor sorting system. Boxes move along a conveyor, and oversized boxes are detected and diverted using a pneumatic pusher. The system includes I/O mapping, a finite state machine (FSM), timers, counters, and safety interlocks.

## Project Structure

```text
project4/
├── README.md
├── requirements.txt
├── io_map.py
├── plc_logic.py
├── conveyor_sim.py
└── output/
    └── conveyor_timeline.png
```

## Implementation

### I/O Mapping

`io_map.py` defines the digital input/output tags and process parameters used by the simulation.

### PLC Logic

`plc_logic.py` implements the core PLC functions, including debounce filtering, rising-edge detection, timers, counters, and the conveyor finite state machine.

### Conveyor Simulation

`conveyor_sim.py` simulates the PLC scan cycle, processes incoming boxes, activates the reject pusher for oversized boxes, and handles emergency stop and manual reset events.

## Running the Project

```bash
pip install numpy matplotlib

python conveyor_sim.py
```

The simulation generates:

```text
output/conveyor_timeline.png
```

## Configuration

| File              | Description                            |
| ----------------- | -------------------------------------- |
| `io_map.py`       | I/O definitions and process parameters |
| `plc_logic.py`    | PLC logic, timers, counters, and FSM   |
| `conveyor_sim.py` | Conveyor simulation and event sequence |

## Output

* Conveyor state transitions
* Box counting and sorting results
* Emergency stop and manual reset events
* Timeline visualization saved in `output/`

## Deliverables

* `io_map.py`
* `plc_logic.py`
* `conveyor_sim.py`
* `output/conveyor_timeline.png`
* Console output demonstrating sorting and safety interlock operation
