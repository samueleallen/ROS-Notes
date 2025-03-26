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
After running the command `roscore`, in a new terminal, run the command: `rosrun turtlesim turtlesim_node`

If we want a behavior diagram of how our turtle simulation is interacting between nodes, we can use the command: `rosrun rqt_graph rqt_graph`
   
### Publishing Data
`rostopic pub [topic] [msg_type] [args]` publishes data onto a topic currently being run.
 * Example: Use the command `rostopic pub /turtle/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'`
     * This publishes the velocity commands at a rate of 1 HZ on the velocity topic
     * Note: The `--` is used to tell the option parser that none of the following arguments is an option. This is required in cases where our arguments may be negative.

## Ros Services
Services are another way that nodes can communicate with one another. 
 * Allows nodes to send a request and receive a response
 * `rosservice list` gets a full list of commands we can use
 * `rosservice type [service]` returns teh arguments the service call takes. If it is empty, that means no arguments are taken.
 * `rosservice call [service] [args]`
 * `rosparam` allows us to store and manipulate data on the ROS parameter server.
     * We can save the parameters we set to a yaml file and load them into new namespaces
     * `rosparam dump [file_name] [namespace]`
     * `rosparam load [file_name] [namespace]`


 
