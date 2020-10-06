# ROS Rosdep

This repository demonstrates the usage of rosdep.

## Installation

`apt` is preferred over `pip` as it is updated automatically and faster.  
```bash
# ROS Noetic
sudo apt-get install python3-rosdep
# ROS Melodic and earlier
sudo apt-get install python-rosdep
```

On non Ubuntu platforms please use `pip`.
```bash
sudo pip install -U rosdep
```

After installation for both `apt` and `pip` please remember to initialize and update it.  
```bash
# Init rosdep
sudo rosdep init
# Update rosdep
rosdep update
```

## Usage for Installing ROS Package

`rosdep` can also be used to install ROS package just as `catkin`.  
```bash
rosdep install my_package
```

## Usage for Dependency Installation

Install dependency of all packages in the workspace.  
```bash
cd catkin_ws
rosdep install --from-paths src --ignore-src -r -y
```

Structure of the directory.  
```bash
catkin_ws/src/
├── costmap_converter
├── costmap_prohibition_layer
├── frontier_exploration
├── move_base_flex
├── move_base_wo_map
├── navigation
├── navigation_layers
├── navigation_msgs
├── p3dx
├── people
├── ros-class-node
├── ros-dynamic-reconfigure
├── ros_gtest
├── rviz-interactive-markers
├── servicesim_competition
├── teb_local_planner
└── wu_ros_tools
```

Install dependency for a directory in a workspace.  
```bash
cd catkin_ws/src
rosdep install --from-paths p3dx --ignore-src -r -y
```

Structure of the directory.  
```bash
src/p3dx/
├── p3dx_control
├── p3dx_description
├── p3dx_gazebo
└── p3dx_viz
```

## Reference

- Installation [link](http://wiki.ros.org/rosdep)