# ros_learn

## 安装ROS

### ros + moveit
参考脚本一键安装
https://github.com/leurekay/ros-install-one-click

## 基本操作
### 创建工作空间

### 创建功能包


## 机械臂

### urdf
- 编写urdf配置文件
- 编写launch文件可视化展示
  
### moveit
- 启动Setup Assistant,导入urdf文件进行配置
  - aaaa
  - bbbb
- 生成***_moveit_config目录
  包含：
  - aaaa
  - bbbb
- 启动编写好的launch文件，

### 控制真实的机械臂
- 单片机上写好通过通过串口，控制各个舵机转动角度的程序
- 启动一个包含发布机械臂各关节角度的程序，例如：
  - roslaunch marm_moviet_config demo.launch    #在rviz中拖动机械臂，planning+excute,界面中的机械臂可以运动到指定点
  - roslunch pro......    #让机械臂末端在rviz中画圆
- 上位机ros订阅其他节点发布的 joint_state,得到各个关节的角度，从而通过串口控制真实的机械臂。
  - rosrun ..........


## 视觉

### 深度相机

### 内参标定

## 手眼标定



