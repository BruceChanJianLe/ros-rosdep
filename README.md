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

## Reference

- Installation [link](http://wiki.ros.org/rosdep)