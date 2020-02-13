# Robot Timing Simulation
Robot Timing Simulation written in C++17

# What it does
1) This measures how long a robot will take to complete a circuit of 1000 or more assigned nodes.
2) It also estimates the minimum amount of time it takes to complete circuit.
3) Uses 3 input files:
  - nodes_input.csv: describes 1000 or more node types.
  - paths_input.csv: describes 1000 or more assigned nodes to be visited by each robot.
  - robots_input.csv: described 4 or more robot types and its speed

# Capability
1) It can schedule more than 1000 assigned nodes to be visited by each robot. For example, it can handle 2000 assigned nodes per circuit, instead of 1000 default count of nodes.  
2) It can schedule more than 4 robots.  For example, it can handle 10 robots, instead of 4 default count. 
3) It can just estimate the minimum run time, without running a real time simulation.
4) It can do a real time simulation.  For example, the default setup of 1000 nodes per robot with 4 robots takes about 50 hours.
5) It can optimize a real time simultion in millisecond timing resolution.  
6) This dramatically reduces the total run time to 2 minutes total from 50 hours.
7) Each robot can have different count of assigned nodes per circuit.
8) and more!
 
# steps to build the app.
```markdown
1. git clone git@github.com:dparksports/RobotTimingSimulation.git
2. cd RobotTimingSimulation
3. mkdir build;cd build
4. cmake..
5. make
6. ./robot 
```

# Output files
```markdown
- visited.csv: a list of nodes tagged with visited robot IDs, in order.
- measuredtimes.csv: a list of measured time of each circuit by each robot ID, in seconds.
```

# Output Log
```markdown
- The output logs each node visited by each robot task and its timing.
- This app also calculates a minium estimated travel time for each robot.
- This app also verifies all assigned nodes in order of each circuit to be visited by a robot.
```

# Timing Scale
- To simulate the actual time in real time, change the current millisecond timing resolution to 'second timing resolution' like this in code.
        std::this_thread::sleep_for(std::chrono::second(travelTime));
- For example, simulating in this robot simulation in real time, in seconds, will take about 50 hours for 1000 assigned nodes per each robot, of all 4 robots.
- The current setup optimizes the real time simulation, by reducing about 50 hours to 2 minutes, by using the timing resolution in milliseconds.

# Code Spec

This code models how long robots will take to complete a circuit of assigned nodes.

There are two types of robots: organizer robots and mover robots. 

Some number of each type of robot will travel along different paths through a common set of nodes. 
Each robot will perform different actions at different nodes which require different amounts of time to complete:

• Organizer robots can perform a pick action (30 sec) and a place action (45 sec).
• Mover robots can perform a push action (20 sec) and a pull action (35 sec).

For the purpose of this challenge there will be two types of nodes: A nodes and B nodes.

At A nodes:
• Organizer robots must perform a pick action.
• Mover robots must perform a push action.

At B nodes:
• Organizer robots must perform a place action.
• Mover robots must perform a pull action.

Robots will follow different paths on the same set of nodes, so it is possible for robots to be at the same node at
the same time. If this happens, whichever robot gets there first gets to perform their action first, and the other
must wait until the first robot has left the node to start their action. In the event of a tie, any Organizer robot can
go first.

This application that takes in 3 csv files and produces two new csv files.

The first file in the input describes the robots: “id,robot_type,speed”. 
The second file describes the nodes: “id,node_type”. 
The last file describes the paths: “robot_id,node_id”. In this file, the order of the rows is the order
of the robot’s node visitation (note: all the robot paths will be in the same file, one after the other).

The first file in the output should report the times for each robot to complete its path. 
Each row should be “robot_id,seconds". 
The second output file should be a list of the visits to each node. 
Each row should be “node_id,robot_id1,robot_id2...” where robot_idN is the Nth robot to have visited the node.

For simplicity that all robots start at the same time from a start node that is separate from the
other nodes, all nodes are equidistant, and speed can be interpreted as the number of seconds it takes to get from
one node to the next.

# Wish List
- Given more time, will revisit the code to comment.  ;)
- Refactor one file into multiple classes to keep it simple.

# License
- MIT License
- Free to do whatever you wish with proper attribution.
- Copyright 2020, all rights served.
