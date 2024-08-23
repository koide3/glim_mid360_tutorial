# MID360

## Livox SDK2

```bash
git clone https://github.com/Livox-SDK/Livox-SDK2.git
cd ./Livox-SDK2/
mkdir build
cd build
cmake .. && make -j4
sudo make install
```


## livox_ros_driver2

```bash
cd ~/ros2_ws/src
git clone https://github.com/Livox-SDK/livox_ros_driver2.git
mv livox_ros_driver2/package_ROS2.xml livox_ros_driver2/package.xml

cd ..
colcon build --cmake-args -DROS_EDITION="ROS2" -DHUMBLE_ROS="humble" --symlink-install
```

```bash
cd ~/ros2_ws/src/livox_ros_driver2/config
nano MID360_config.json
# "host_net_info" ->  "192.168.1.5"  ->  your IP
# "lidar_configs/ip" -> "192.168.1.12"  ->  "192.168.1.1XX"
```

## Connection

```bash
koide@ubuntu:~/ros2_ws/src/livox_ros_driver2/config$ ping 192.168.1.182
# PING 192.168.1.182 (192.168.1.182) 56(84) bytes of data.
# 64 bytes from 192.168.1.182: icmp_seq=1 ttl=255 time=0.750 ms
# 64 bytes from 192.168.1.182: icmp_seq=2 ttl=255 time=1.31 ms
# 64 bytes from 192.168.1.182: icmp_seq=3 ttl=255 time=1.74 ms
```

```bash
source ~/.bashrc
ros2 launch livox_ros_driver2 rviz_MID360_launch.py
```


## GLIM

```bash
sudo apt update
sudo apt install -y gpg curl
```


```bash
curl -s https://koide3.github.io/ppa/setup_ppa.sh | sudo bash
```

```bash
sudo apt update
sudo apt install -y ros-humble-glim-ros-cuda12.5
sudo ldconfig
```

```bash
cp -R /opt/ros/humble/share/glim/config .
nano config/config_ros.json
# "acc_scale": 9.81
# "imu_topic" : "/livox/imu"
# "points_topic" : "/livox/lidar"

nano config/config_preprocess.json
# "random_downsample_target": 5000
```
