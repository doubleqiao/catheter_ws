# catheter_ws
Control of the catheter

# source
source: there are some functions used to simplify the operations, and this file is hiden in Toan's computer.
~/.bash_source

source catheter_ws/devel/setup.bash

The catheter_ws workspace is built based on the source of soem and ndi_hardware.

catheter_ws/ndi_hardware/soem

# deploy the component from the script or the ops
. ./cath_bending_control/run.sh
or in the directory that the run.sh is in  ./run.sh

# Problem-solved
The config/Slave_1001.xml should be put in the same package as cath_bending_control
otherwise you will have problems such as 
[Connect] Could not load configuration from config/Slave_1001.xml
"No such port: 'Valve X' while looking for port 'Master.slave.Valve X'"

# Problem-unsolved
In the orocos deployment manuel, the statement path and import have some differences on "whether search the subdirectories" and "whether it is the preload or directly load". My question is whether the import searches all the paths or the path searched is indicated by the $ROS_ACKAGE_PATH?

# Some learning aspects-ROS

## Why we often need to do "source devel/setup.sh"? 
In ROS, the ROS_PACKAGE_PATH is used for the ROS system to search packages, and that is why we need to do the source. The goal of source is to change the environmental variable ROS_PACKAGE_PATH to include the path where your workspace or the packages are in.

## Workspace overlay

### Why workspace overlay?
Normally only **one** workspace's path can be added to the environment variable ROS_PACKAGE_PATH, which is the searching path of ROS and is changed by "source path_of_workspace/devel/setup.sh".

In order to achieve "communication" between different workspaces,different workspaces can be overlayed, which means the paths of multiple workspaces can be added to the environment variable ROSPACKAGE_PATH.

### How to do workspace overlay?
After making sure that the path of the workspace (for example workspace A) you want to "communicate" with is included in the ROS_PACKAGE_PATH, then build the workspace at hand (workspace B) by using catkin_make in the same terminal. Then do "source path_of_workspace_B/devel/setup.sh". By using "echo $ROS_PACKAGE_PATH" you will see the path list as "path_of_workspace_B/src: path_of_workspace_A/src: ...". In the same terminal, you can build the wrokspace C then. 

The same rule applies for multiple workspaces.


# Some learning aspects-OROCOS
In Orocos, the deployment component do the following things:
- import--load or preload the library (something like the classes, or they call it the types)
- load -- create the specific instance (maybe is the object) with the name and type
- configure
- start
