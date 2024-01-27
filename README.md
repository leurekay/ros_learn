# ros_learn

## 安装ROS

### ros + moveit
参考脚本一键安装
https://github.com/leurekay/ros-install-one-click

## 基本操作
- 创建工作空间
- 创建功能包
- catkin_make
- 查看所有topic
- rostopic echo /joint_states
  


## 机械臂

### urdf
- 编写urdf配置文件
- 编写launch文件可视化展示
  roslaunch marm_description  view_marm.launch
  
### moveit
- 启动Setup Assistant,导入urdf文件进行配置:rosrun moveit_setup_assistant moveit_setup_assistant
  - aaaa
  - group
    - solver:kdl
    - ompl planning: rrt
  - group,机械臂和夹住是两个不同的组
- 生成***_moveit_config目录
  包含：
  - aaaa
  - bbbb
- 启动编写好的launch文件，

### 控制真实的机械臂
- 单片机上写好通过通过串口，控制各个舵机转动角度的程序
- 启动一个包含发布机械臂各关节角度的程序，例如：
  - roslaunch marm_moveit_config demo.launch    #在rviz中拖动机械臂，planning+excute,界面中的机械臂可以运动到指定点
  - rosrun probot_demo moveit_circle_demo.py  #让机械臂末端在rviz中画圆
  - rosrun real_arm move_subscribe.py  #吸盘版本，订阅其他节点发布的3d位置坐标，机械臂末端移动该位置
    - public coordinate (x,y,z) by command line: rostopic pub /move_coordinates geometry_msgs/Point '{x: -0.1, y: -0.05, z: 0.04}'
- 上位机ros订阅其他节点发布的 joint_state,得到各个关节的角度，从而通过串口控制真实的机械臂。
  - rosrun real_arm nanoarm_bringup.py
  - rosrun real_arm sucker_bringup.py  #吸盘版本


## 视觉
rqt_image_view

### 深度相机
#### install qudong
#### launch
roslaunch astra_camera astra.launch


### 内参标定
install
sudo apt install ros-noetic-camera-calibration

launch camera:
roslaunch probot_vision usb_cam.launch


rosrun camera_calibration cameracalibrator.py  --size 8x6 --square 0.02 image:=/usb_cam/image_raw camera:=/usb_cam

### 手眼标定
#### 采集数据
- 发布坐标位置话题，同时记录下末端link相对于base_link的tf,同时保存摄像头拍的标定版图片
- 启动moveit移动到指定位置的程序
  - rosrun real_arm move_subscribe.py
- 启动控制真实的机械臂的节点
  - rosrun real_arm sucker_bringup.py
  

#### AX=XB



