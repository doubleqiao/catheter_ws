# catheter_ws
Control of the catheter

# source
source: there are some functions used to simplify the operations, and this file is hiden in Toan's computer.
~/.bash_source

source catheter_ws/devel/setup.bash

The catheter_ws workspace is built based on the source of soem and ndi_hardware.

catheter_ws/ndi_hardward/soem

# deploy the component from the script or the ops
. ./cath_bending_control/run.sh
or in the directory that the run.sh is in  ./run.sh

# Problem-solved
The config/Slave_1001.xml should be put in the same package as cath_bending_control
otherwise you will have problems such as 
[Connect] Could not load configuration from config/Slave_1001.xml
"No such port: 'Valve X' while looking for port 'Master.slave.Valve X'"

# Problem-unsolved
In the orocos deployment manuel, the statement path and import have some differences on "whether search the subdirectories" and "whether it is the preload or directly load". My question is whether the import searches all the paths or the path searched is indicated by the $ROS_pACKAGE_PATH?



# Some learning aspects-ROS
In ROS, the ROS_PACKAGE_PATH is used for the ROS system to search packages, and that is why we need to do the source. The goal of source is to change the environmental variable ROS_PACKAGE_PATH to include the path where your workspace or the packages are in.

# Some learning aspects-OROCOS
In Orocos, the deployment component do the following things:
- import--load or preload the library (something like the classes, or they call it the types)
- load -- create the specific instance (maybe is the object) with the name and type
- configure
- start
