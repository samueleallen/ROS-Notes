# Basic Commands and Information

Important Terms:
 * Packages: Fundamental units of software organization.
     * Basically is a directory that holds our code, data, and documentation
 * Nodes: An executable that uses ROS to communicate with other nodes
 * Messages: ROS data type used when subscribing or publishing a topic
 * Topics: Nodes can _publish_ messages to a topic as well as _subscribe_ to a topic to receive messages
 * Master: Name service for ROS (i.e. helps nodes find each other)
 * Roscore: Master + rosout + parameter server
     * First thing you should run when using ROS

May also need to source the environment setup file for our workspace. Example given below
`cd ~/catkin_ws/
 source devel/setup.bash
 roscd beginner_tutorials`
   
## Turtle Sim
After running the command `roscore`, in a new terminal, run the command: `rosrun turtlesim turtlesim_node`

If we want a behavior diagram of how our turtle simulation is interacting between nodes, we can use the command: `rosrun rqt_graph rqt_graph`
   
### Publishing Data
`rostopic pub [topic] [msg_type] [args]` publishes data onto a topic currently being run.
 * Example: Use the command:
   `rostopic pub /turtle/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, -1.8]'`
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

## RQT Console and RosLaunch
`rqt_console` and `rqt_logger_level` are useful for debugging; whereas, `roslaunch` is useful tool for starting many nodes at once.
 * RQT Console is used to help display output from nodes.
     * Run the console with `rosrun rqt_console rqt_console`
 * RQT Logger Levels allow us to change the verbosity level (DEBUG, WARN, INFO, and ERROR) of nodes as they run.
     * Run the logger level with `rosrun rqt_logger_level rqt_logger_level`
     * Logging levels are priortized in this order: Fatal, Error, Warn, Info, Debug
     * When we set the logger level, we get all messages of that priority level **or** higher

Roslaunch starts nodes as defined in a launch file
 * `roslaunch [package] [filename.launch]

Creating a launch file:
 1. Source the environment (If Needed)
 2. `roscd [package_name]`
 3. Make a launch directory and go to it
      * `mkdir launch`
      * `cd launch`
 4. Now make a launch file
      * `touch [file_name].launch`
 5. Edit launch file as wanted

## Using Rosed (ROS Edit)
Allows you to directly edit a file within a package by using package name rather than annoyingly typing the entire path to the package.
`rosed [package_name] [filename]`

Auto completing with hitting tab twice can let us easily see and optionally edit all files from a package without knowing its exact name.
`rosed [package_name] <tab><tab>

Default Editor for rosed is vim. We can change this to nano editor (auto-installed with ubuntu) with the commands:
`export EDITOR='nano -w'`

## Creating ROS msg and srv
 * msg: a msg file is a simple text file that describes the fields of a ROS message. Used to generate source code for messages in different languages.
     * Stored in msg directoy of a package
     * In a msg file, you specify each line with a field type and field name. Field types include int8, int16, ... , string, time, float, etc. 
 * srv: an srv file describes a service.
     * Composed of two parts: a request and a response
     * Stored in srv directory of a package
     * Just like a masg file except they contain two parts, a request and a response separated by a '---'

