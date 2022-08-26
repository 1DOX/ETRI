

# MAP Saver

### **T1**) RUN turtlebot3 world with gazebo
> ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

### **T2**) RVIZ Map Drawing
> ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True

### **T3**) Teleop
> ros2 run turtlebot3_teleop teleop_keyboard

### **T4**) Map Saver - path는 파일경로/파일이름 (확장자 제외)
> ros2 run nav2_map_server map_saver_cli -f <path>
>> ros2 run nav2_map_server map_saver_cli -f ~/map `root 아래에 map.yaml, map.pgm`


</br>


# Navigation

### **T1**) RUN turtlebot3 world with gazebo
> ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

### **T2**) State Publisher
> ros2 launch turtlebot3_bringup turtlebot3_state_publisher.launch.py

### **T3**) Navigation Task
> ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=<path/map.yaml>
> ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=/root/seocho.yaml
>> RVIZ 실행되면 2D Pose Estimate(초기위치), Naviagtion2 Goal(목표위치) 설정 (Navigate)


**turtlebot default world**
`/root/turtlebot3_ws/src/turtlebot3/turtlebot3_navigation2/map/turtlebot3_world.yaml`

**LG seocho world**
`/root/seocho.yaml`


</br>


# CLOiSim seocho world + Turtlebot3 [Fail]

`World PATH: /opt/resources/worlds/lg_seocho.world`
`Model PATH: /opt/resources/models`

nav2 - full launch
turtlebot3 - bringup.launch


ros2 launch nav2_bringup tb3_simulation_launch.py

gzserver --verbose -s libgazebo_ros_init.so -s libgazebo_ros_factory.so ~/turtlebot3_ws/src/turtlebot3_simulations/turtlebot3_gazebo/worlds/lg_seocho.world



## turtlebot3_wafle URDF path
/root/turtlebot3_ws/src/turtlebot3/turtlebot3_description/urdf/turtlebot3_waffle.urdf


## turtlebot3(multiple) spawn
ros2 run robot_spawner_pkg spawn_turtlebot waffle turtlebot2 0.0 0.0 0.1

> https://zmk5.github.io/general/demo/ros2-spawning-entity/#node-for-spawning-your-own-entities
