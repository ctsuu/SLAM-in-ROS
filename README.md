# SLAM-in-ROS
SLAM in ROS environment

## Install gmapping
```
$ rospack find gmapping

$ sudo apt-get install ros-kinetic-gmapping
```

http://wiki.ros.org/slam_gmapping/Tutorials/MappingFromLoggedData
```
$ rosmake gmapping

$ roscore

$ rosparam set use_sim_time true

$ rosrun gmapping slam_gmapping scan:=base_scan _odom_frame:=odom_combined
```

