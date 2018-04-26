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

# Problem
The config/Slave_1001.xml should be put in the same package as cath_bending_control
otherwise you will have problems such as 
[Connect] Could not load configuration from config/Slave_1001.xml
"No such port: 'Valve X' while looking for port 'Master.slave.Valve X'"




