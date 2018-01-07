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
## Install Cartographer

https://google-cartographer-ros.readthedocs.io/en/latest/
```
## Install wstool and rosdep.
sudo apt-get update
sudo apt-get install -y python-wstool python-rosdep ninja-build

## Create a new workspace in 'catkin_ws'.
mkdir catkin_ws
cd catkin_ws
wstool init src

## Merge the cartographer_ros.rosinstall file and fetch code for dependencies.
wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall
wstool update -t src

## Install proto3.
src/cartographer/scripts/install_proto3.sh

## Install deb dependencies.
## The command 'sudo rosdep init' will print an error if you have already
## executed it since installing ROS. This error can be ignored.
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y

## Build and install.
catkin_make_isolated --install --use-ninja
source install_isolated/setup.bash
```
## SLAM Rosbag play
```
# Download the 2D backpack example bag.
wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag

# Launch the 2D backpack demo.
roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag
```

```
# Download the 3D backpack example bag.
wget -P ~/Downloads https://storage.googleapis.com/cartographer-public-data/bags/backpack_3d/b3-2016-04-05-14-14-00.bag

# Launch the 3D backpack demo.
roslaunch cartographer_ros demo_backpack_3d.launch bag_filename:=${HOME}/Downloads/b3-2016-04-05-14-14-00.bag
```

