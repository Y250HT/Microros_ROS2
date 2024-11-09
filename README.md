# microros_ws_ros2
The Microros chassis host program for our robot helps you communicate with the esp32 on the chassis and the microros control program on it.

## Install dependencies
```bash
cd ~/microros_ws_ros2/
rosdep update
rosdep install --from-paths src --ignore-src -r -y --rosdistro humble
colcon build
```
Maybe you'll need clash to speed things up, because microros programs need to clone other dependencies from github.

## If your chassis is connected via wifi
```bash
. install/setup.bash
ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888 -v6
```
## If your chassis is connected through a serial port
```bash
sudo chmod 777 /dev/ttyACM*
. install/setup.bash
ros2 run micro_ros_agent micro_ros_agent serial -b 115200 --dev /dev/ttyACM0 -v6
```
## How to test
You can use teleop_twist_keyboard to test(ikjl,)
```bash
sudo apt-get install ros-humble-teleop*
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
