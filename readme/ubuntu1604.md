# Ubuntu 16.04 Build of QuanergyClientRos

## Install QuanergyClient (SDK)

If you haven't already, build QuanergyClient (SDK) per the provided instructions (readme/ubuntu1604.md)
Install QuanergyClient

```
cd ~/QuanergySystems/quanergy_client/build
sudo make install
```
## Install ROS Kinetic RVIZ and configure environment. [official documentation](http://wiki.ros.org/kinetic/Installation/Ubuntu)

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
sudo apt-get update
sudo apt-get install libvtk6-dev ros-kinetic-rviz ros-kinetic-pcl-ros ros-kinetic-rosbash
sudo apt-get install libhdf5-openmpi-dev
source /opt/ros/kinetic/setup.bash
```
## Build Instructions
Clone the ROS SDK repository

```
mkdir -p ~/QuanergySystems/catkin_ws/src
cd ~/QuanergySystems/catkin_ws/src
catkin_init_workspace
git clone https://github.com/QuanergySystems/quanergy_client_ros.git
```
Build QuanergyClientRos

```
cd ~/QuanergySystems/catkin_ws
catkin_make
```
## Testing Build

```
source /opt/ros/kinetic/setup.bash
source ~/QuanergySystems/catkin_ws/devel/setup.bash
roslaunch quanergy_client_ros client.launch host:=<hostname_or_ip>
```
In a separate terminal, the following commands will show the output rate you are getting from your sensor.
```
source /opt/ros/kinetic/setup.bash
rostopic hz /quanergy/points
```


## Optional Configuration
To add ROS environment configuration automatically to every future bash session
```
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
echo "source ~/QuanergySystems/catkin_ws/devel/setup.bash" >> ~/.bashrc
```
