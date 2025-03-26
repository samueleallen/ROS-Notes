# Basic Commands and Information

Important Terms:
 * Packages: Fundamental units of software organization.
     * Basically is a directory that holds our code, data, and documentation
 * Nodes: An executable that uses ROS to communicate with other nodes
 * Messages: ROS data type used when subscribing or publishing a topic
 * Topics: Nodes can _publish_ messages to a topic as well as _subscribe_ to a topic to receive messages
 * Master: Name service for ROS (i.e. helps nodes find each other)
 * `Roscore`: Master + rosout + parameter server
     * Note: Need to figure out more about this term
     * First thing you should run when using ROS
   
## Turtle Sim
After running the command `roscore`, run the command:
$$`rosrun turtlesim turtlesim_node`
   
