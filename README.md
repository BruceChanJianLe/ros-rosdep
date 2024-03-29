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
# If you are ros2 you may want to run the following
rosdep install --from-paths src --rosdistro galactic --ignore-src -y
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

## Other Usage

```bash
Usage: rosdep [options] <command> <args>

Commands:

rosdep check <stacks-and-packages>...
  check if the dependencies of package(s) have been met.

rosdep install <stacks-and-packages>...
  download and install the dependencies of a given package or packages.

rosdep db
  generate the dependency database and print it to the console.

rosdep init
  initialize rosdep sources in /etc/ros/rosdep.  May require sudo.

rosdep keys <stacks-and-packages>...
  list the rosdep keys that the packages depend on.

rosdep resolve <rosdeps>
  resolve <rosdeps> to system dependencies

rosdep update
  update the local rosdep database based on the rosdep sources.

rosdep what-needs <rosdeps>...
  print a list of packages that declare a rosdep on (at least
  one of) <rosdeps>

rosdep where-defined <rosdeps>...
  print a list of yaml files that declare a rosdep on (at least
  one of) <rosdeps>

rosdep fix-permissions
  Recursively change the permissions of the user's ros home directory.
  May require sudo.  Can be useful to fix permissions after calling
  "rosdep update" with sudo accidentally.
```

## Other Options

```bash
Options:
  -h, --help            show this help message and exit
  --os=OS_NAME:OS_VERSION
                        Override OS name and version (colon-separated), e.g.
                        ubuntu:lucid
  -c SOURCES_CACHE_DIR, --sources-cache-dir=SOURCES_CACHE_DIR
                        Override /home/isera2/.ros/rosdep/sources.cache
  -v, --verbose         verbose display
  --version             print just the rosdep version, then exit
  --all-versions        print rosdep version and version of installers, then
                        exit
  --reinstall           (re)install all dependencies, even if already
                        installed
  -y, --default-yes     Tell the package manager to default to y or fail when
                        installing
  -s, --simulate        Simulate install
  -r                    Continue installing despite errors.
  -q                    Quiet. Suppress output except for errors.
  -a, --all             select all packages
  -n                    Do not consider implicit/recursive dependencies.  Only
                        valid with 'keys', 'check', and 'install' commands.
  -i, --ignore-packages-from-source, --ignore-src
                        Affects the 'check', 'install', and 'keys' verbs. If
                        specified then rosdep will ignore keys that are found
                        to be catkin or ament packages anywhere in the
                        ROS_PACKAGE_PATH, AMENT_PREFIX_PATH or in any of the
                        directories given by the --from-paths option.
  --skip-keys=SKIP_KEYS
                        Affects the 'check' and 'install' verbs. The specified
                        rosdep keys will be ignored, i.e. not resolved and not
                        installed. The option can be supplied multiple times.
                        A space separated list of rosdep keys can also be
                        passed as a string. A more permanent solution to
                        locally ignore a rosdep key is creating a local rosdep
                        rule with an empty list of packages (include it in
                        /etc/ros/rosdep/sources.list.d/ before the defaults).
  --filter-for-installers=FILTER_FOR_INSTALLERS
                        Affects the 'db' verb. If supplied, the output of the
                        'db' command is filtered to only list packages whose
                        installer is in the provided list. The option can be
                        supplied multiple times. A space separated list of
                        installers can also be passed as a string. Example:
                        `--filter-for-installers "apt pip"`
  --from-paths          Affects the 'check', 'keys', and 'install' verbs. If
                        specified the arguments to those verbs will be
                        considered paths to be searched, acting on all catkin
                        packages found there in.
  --rosdistro=ROS_DISTRO
                        Explicitly sets the ROS distro to use, overriding the
                        normal method of detecting the ROS distro using the
                        ROS_DISTRO environment variable. When used with the
                        'update' verb, only the specified distro will be
                        updated.
  --as-root=INSTALLER_KEY:<bool>
                        Override whether sudo is used for a specific
                        installer, e.g. '--as-root pip:false' or '--as-root
                        "pip:no homebrew:yes"'. Can be specified multiple
                        times.
  --include-eol-distros
                        Affects the 'update' verb. If specified end-of-life
```

## Reference

- Installation [link](http://wiki.ros.org/rosdep)
