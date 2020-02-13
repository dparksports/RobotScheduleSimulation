# RobotTimingSimulation
Robot Timing Simulation written in C++17

# What it does
1) This measures how long a robot will take to complete a circuit of 1000 or more assigned nodes.
2) This estimates the minimum amount of time it takes to compplete circuit, before a simulation run.
3) Uses 3 input files:

a) nodes_input.csv: describes 1000 or more node types.
b) paths_input.csv: describes 1000 or more assigned nodes to be visited by each robot.
c) robots_input.csv: described 4 or more robot types and its speed




# Requirements

This code models how long simpleton robots will take to complete a circuit. 

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
