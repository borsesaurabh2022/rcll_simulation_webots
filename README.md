# RCLL Simulation (Webots)

Webots simulation of Festo Robotino robots and MPS machines for the RoboCup Logistics League (RCLL), connected to ROS 2 through `webots_ros2_driver`.

Fork of [carologistics/rcll_simulation_webots](https://github.com/carologistics/rcll_simulation_webots). Detailed documentation is in the [upstream wiki](https://github.com/carologistics/rcll_simulation_webots/wiki).

## Packages
| Package | Contents |
|---|---|
| `robotino_simulation` | Webots worlds, Robotino protos, simulation driver and launch files |
| `mps_description` | Models of the Festo MPS machines (base, cap, ring, storage, delivery) |

## Requirements
- Ubuntu 24.04, ROS 2 Jazzy
- Webots R2023b with `webots_ros2_driver`
- `vcstool` for the dependencies in `dependencies.repos`

## Build
```bash
source /opt/ros/jazzy/setup.bash
mkdir -p ~/ros2_ws/src && cd ~/ros2_ws
git clone https://github.com/borsesaurabh2022/rcll_simulation_webots.git src/rcll_simulation_webots
vcs import src < src/rcll_simulation_webots/dependencies.repos
rosdep install --from-paths src --ignore-src -y
colcon build --symlink-install
source install/setup.bash
```

## Run
```bash
# One Robotino (worlds exist for robotinobase1, 2 and 3)
ros2 launch robotino_simulation robotino_simulation.launch.py namespace:=robotinobase1

# Three Robotinos in one arena
ros2 launch robotino_simulation robotinocluster_simulation.launch.py
```

## License
MIT, see [LICENSE](LICENSE).
