# Omnidirectional Robot Odometry
Omnidirectional 4-wheels mobile robot odometry implementation in ROS (C++) as "Robotics" course project 2022, Politecnico di Milano.

Real Robot                 |  Robot Scheme
:-------------------------:|:-------------------------:
![](img/real.png)          |  ![](img/scheme.png)

## 1. Authors
- Alessandro Restifo, 10608696
- Mirko Usuelli, 10570238

## 2. Archive files descriptions
```
omni-robot/
.
├── bags
│   ├── bag1.bag
│   ├── bag2.bag
│   └── bag3.bag
├── cfg
│   └── parameters.cfg
├── CMakeLists.txt
├── config
│   └── omni_config.yaml
├── include
│   ├── omni_odometry.h
│   ├── omni_params
│   ├── omni_reset.h
│   └── omni-robot
│       ├── omni_model.h
│       └── omni_tester.h
├── launch
│   └── omni-robot.launch
├── package.xml
├── README.md
├── script
│   └── plot_result.py
├── src
│   ├── omni_model.cpp
│   ├── omni_model_node.cpp
│   ├── omni_odometry.cpp
│   ├── omni_reset.cpp
│   ├── omni_tester.cpp
│   └── omni_tester_node.cpp
└── srv
    └── omni_reset.srv
```
// TODO: aggiornare albero + descrizione dell'architettura: esempio ci sono due nodi ros, il primo nodo fa una cosa, il secondo un'altra ...etc...

## 3. Names and meaning of the ROS parameters
// TODO: chiedere a cudrano

## 4. TF tree
![](img/tf.jpg)

## 5. Custom Messages
- omni_msg.msg : used to publish rpm wheels information for second task (which will be subscribed by the second node "omni_tester")
```
    Header header
    float64 rpm_fl
    float64 rpm_fr
    float64 rpm_rr
    float64 rpm_rl
```

## 6. Instrucions
- Insert the ROS packages by typing:
```
  $ mv omni-robot <path>/catkin_ws/src
```
- Go to your own *catkin_ws* folder in the system and recompile everything by doing:
```
  $ cd <path>/catkin_ws
  $ source ./devel/setup.bash
  $ catkin_make
```
- Then run `ROS core` by typing:
```
  $ roscore
```
- Open a new terminal and launch the robot simulation as:
```
  $ cd <path>/catkin_ws
  $ source ./devel/setup.bash
  $ roslaunch omni-robot omni-robot.launch
```
### (I) Compute Odometry
- Open one terminal and start rviz:
```
  $ rviz
```
- Launch the launch file:
```
  $ roslaunch omni_robot omni_robot.launch
```
- Execute a bag file:
```
  $ rosbag play <bag_file>.bag
```
![](img/goal_1.gif)

### (II) Compute Control
- Open one terminal and start plotjugger:
```
  $ rosrun plotjugger plotjugger
```
- Launch the launch file:
```
  $ roslaunch omni_robot omni_robot.launch
```
- Execute a bag file:
```
  $ rosbag play <bag_file>.bag
```
![](img/goal_2.gif)

### (III) Reset Service
- Launch the launch file:
```
  $ roslaunch omni_robot omni_robot.launch
```
- Execute a bag file:
```
  $ rosbag play <bag_file>.bag
```
- Open another terminal and whenever you want type, for instance x=0, y=0, theta=0:
```
  $ rosservice call /reset 0 0 0
```
![](img/goal_3.gif)

### (IV) Dynamic Configuration for the Integration Method
- Launch the launch file:
```
  $ roslaunch omni_robot omni_robot.launch
```
- Open one terminal and start rqt_configure:
```
  $ rosrun rqt_reconfigure rqt_reconfigure
```
- Execute a bag file:
```
  $ rosbag play <bag_file>.bag
```
![](img/goal_4.gif)

## 7. Further info
// TODO: genetic algortihms + images
