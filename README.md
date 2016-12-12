# TurtleSwarmMapper

3D Exploration from 2 robots, sharing their map when detecting each other

## gazebo_concert_yanik
own simulation for gazebo with 2 turtlebots

> roslaunch gazebo_concert_yanik concert.launch --screen
> rocon_remocon

- Dependencies : gazebot_concert
- Tutorial : http://wiki.ros.org/gazebo_concert

## yanik_concert
own concert

services : 
* Admin
* teleop
* chatter (add "Yanik Concert" to the whitelist of Chatter_concert) 

> rocon_launch yanik_concert start_solution_and_robot.concert --screen
> rocon_remocon

- Dependencies : concert_master
- Tutorial : http://wiki.ros.org/rocon_concert/Tutorials/indigo/Create%20Your%20Own%20Solution

## Multi-robot-simulation
launcher for stage world with 2 robots, mapping, move_base and sharing data in each of them

> roslaunch multi-robot-simulation master.launch
> rosservice call /robot_0/adhoc_communication/join_mc_group mc_robot_1 1
> rosservice call /robot_0/adhoc_communication/send_twist "dst_robot: 'robot_1'
topic: '/cmd_vel'
twist:
  linear:
    x: 1.0
    y: 0.0
    z: 0.0
  angular:
    x: 0.0
    y: 0.0
    z: 0.0" 

- Dependencies : stage_ros, gmapping, move_base, adhoc_communication
- Tutorial : http://wiki.ros.org/adhoc_communication

## tsm_nav
launcher for real turtlebot with rplidar node, gmapping, move_base

>roslaunch tsm_nav bringup_map_move.launch

- Dependencies : rplidar_node, turtlebot_le2i, gmapping, move_base

## tsm_share_maps
launcher for map exchange through adhoc_communication 

- Dependencies : adhoc_communication
