# Lidar Graph Slam

this is a graph slam tutorial which generates point cloud map using slam. This package is a simple enough mapping tool with decent accuracy.

![](https://s2.ax1x.com/2019/05/25/Vkfogx.md.png)

## Install

Before start mapping using this package, install some dependencies first:

```
# for kinetic
sudo apt-get install ros-kinetic-geodesy ros-kinetic-pcl_ros ros-kinetic-nmea-msgs ros-kinetic-libg2o
# for melodic
sudo apt-get install ros-melodic-geodesy ros-melodic-pcl_ros ros-melodic-nmea-msgs ros-melodic-libg2o

cd catkin_ws/src
git clone https://github.com/koide3/ndt_omp.git
```

After `catkin_make` successful, start mapping:

1. Bag file (recorded in an outdoor environment):
- [hdl_400.bag.tar.gz](http://www.aisl.cs.tut.ac.jp/databases/hdl_graph_slam/hdl_400.bag.tar.gz) (raw data, about 900MB)

`terminal 1`:
```bash
rosparam set use_sim_time true
roslaunch hdl_graph_slam hdl_graph_slam_400.launch
```
`terminal 2`
```bash
roscd hdl_graph_slam/rviz
rviz -d hdl_graph_slam.rviz
```
`terminal 3`
```bash
rosbag play --clock hdl_400.bag
```

2. After mapping, save map

`terminal 4`
```
rosservice call /hdl_graph_slam/save_map "resolution: 0.05
destination: '/media/jintian/data/map_out.pcd'"
```
