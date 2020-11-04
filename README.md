# yolov5_record
    - based on tf/pytorch
## unload original CUDA 10.0
    - cd /usr/local/cuda-10.0/bin/
    - sudo ./uninstall_cuda_10.0.pl
    - sudo rm -rf /usr/local/cuda-8.0/
## check 对应cuda版本
    - https://pytorch.org/
## 官网下载对应版本CUDA
    - https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal
    - （实测deb版本最稳定）
    - 安装报错 https://blog.csdn.net/wanttifa/article/details/107548931
    -配置环境变量
    gedit ~/.bashrc
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64
    export PATH=$PATH:/usr/local/cuda-10.1/bin
    export CUDA_HOME=/usr/local/cuda-10.1
    source ~/.bashrc更新

    sudo /usr/local/cuda-9.1/bin/uninstall_cuda_9.1.pl
    - nivdia驱动重新配置
    sudo dkms install -m nvidia -v 418.87
    -修复环境变量问题
    https://blog.csdn.net/qingfenglu/article/details/80388522
    https://blog.csdn.net/qq_15265729/article/details/85201786

    - cudnn安装
    https://blog.csdn.net/wanzhen4330/article/details/81704474
    sudo chmod +r libcudnn.so.8.0.2
    sudo ln -sf libcudnn.so.8.0.2 libcudnn.so.8  
    sudo ln -sf libcudnn.so.8 libcudnn.so     
    sudo ldconfig

     sudo ldconfig /usr/local/cuda-10.1/lib64

     tar -xzvf cudnn-10.1-linux-x64-v8.0.2.39.tgz
     https://blog.csdn.net/IT_zxl001/article/details/89350373#commentBox
     (据说cudnn版本8之后无法按原方式显示版本）

 ### 所以为啥要卸载重安23333....就很气<>
     - https://blog.csdn.net/qq_38163755/article/details/88353898 (适合deb版本CUDA10.1)
     https://blog.csdn.net/mbytes/article/details/102901486?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param#cuda_75(run版本10.2)
     - chmod a+x cuda_10.2.89_440.33.01_linux.run
     - sudo sh cuda_10.2.89_440.33.01_linux.run
     - sudo gedit .bashrc 等
     - 再次卸载CUDNN
     - 再次安装CUDNN
     tar -xzvf cudnn-10.2-linux-x64-v8.0.3.33.tgz
     dohbless@dohbless-G3-3579:~/下载/cuda$ sudo cp lib64/lib* /usr/local/cuda/lib64/

     sudo chmod +r libcudnn.so.8.0.3
     sudo ln -sf libcudnn.so.8.0.3 libcudnn.so.8
     sudo ln -sf libcudnn.so.8 libcudnn.so     
     sudo ldconfig
     cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
#### 开始重新安装10.2
(这次是提前下好的.run文件啦)
#### 测试之前安好的pytorch
    lirui@lirui:~/下载$ python
    Python 3.6.4 |Anaconda, Inc.| (default, Jan 16 2018, 18:10:19) 
    [GCC 7.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import torch
    >>> 
    木有报错嘻嘻
## pip 安装pytorch
    pip install torch==1.6.0+cu101 torchvision==0.7.0+cu101 -i  https://pypi.tuna.tsinghua.edu.cn/simple
    pip install torch==1.6.0+cu101 torchvision==0.7.0+cu101 -i http://pypi.douban.com/simple/
    https://download.pytorch.org/whl/torch_stable.html
    pip --default-timeout=100 install torch torchvision -i  https://pypi.tuna.tsinghua.edu.cn/simple
    https://blog.csdn.net/qq_15192373/article/details/104244743 简单直白
## realsense相机驱动安装
    https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md
    shell执行命令
    realsense-viewer
## ros系统安装
    - 第一个：sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
    - 第二个：sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
    - 第三个：
    sudo apt update
    sudo apt install ros-melodic-desktop-full
    - 第四个：
    sudo rosdep init
    rosdep update
    如果失败：#打开hosts文件
    sudo gedit /etc/hosts
    #在文件末尾添加
    151.101.84.133 raw.githubusercontent.com
    #保存后退出再尝试
    来自：https://blog.csdn.net/u013468614/article/details/102917569
    - 第五个：
    echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
    source ~/.bashrc
    - 最后一个：
    sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential
### apt和dpkg区别
    - 两者的区别是dpkg绕过apt包管理数据库对软件包进行操作，所以你用dpkg安装过的软件包用apt可以再安装一遍，系统不知道之前安装过了，将会覆盖之前dpkg的安装。
    - 1、dpkg是用来安装.deb文件,但不会解决模块的依赖关系,且不会关心ubuntu的软件仓库内的软件,可以用于安装本地的deb文件。
    - 2、apt会解决和安装模块的依赖问题,并会咨询软件仓库, 但不会安装本地的deb文件, apt是建立在dpkg之上的软件管理工具。
### ROS+python3+cv_brige
    - https://zhuanlan.zhihu.com/p/77682229
    - https://www.jianshu.com/p/2f86607c98d1
    - https://www.jianshu.com/go-wild?ac=2&url=https%3A%2F%2Fblog.csdn.net%2Flightnateriver%2Farticle%2Fdetails%2F97794261
    - https://www.it610.com/article/1279274013260005376.htm
### 出现错误ModuleNotFoundError: No module named 'defusedxml'
    - sudo ln -s /usr/bin/python2.7 /usr/bin/python
    - https://blog.csdn.net/wangguchao/article/details/82151372
    - https://blog.csdn.net/java0fu/article/details/106081845?utm_medium=distribute.pc_relevant.none-task-blog-title-3&spm=1001.2101.3001.4242
### 启动ros节点(ctrl+alt+t打开终端 /rosrun运行节点)
    roscore
    rosrun turtlesim turtlesim_node
    rosrun turtlesim turtle_teleop_key
### ros学习(tab补全）
    https://blog.csdn.net/weixinhum/article/details/83026236
    rqt_graph
    rosnode list    rosnode info /turtlesim    
    rostopic list
    rostopic pub /turtel/cmd_vel
    - rostopic pub -r 10 /turtle1/cmd_vel geometry_msgs/Twist  "linear  （话题相关）
    - rosservice ....(服务相关)
    - rosbag 记录话题工具
       rosbag record -a -O cmd_record
       rosbag play ....
### ros创建工作空间和工作包
    mkdir catkin_ws
    cd catkin_ws/
    mkdir src
    cd src/
    catkin_init_workspace
    (编译)
    cd ..
    catkin_make
    catkin_make install
    (创建工作包)
    cd src/
    catkin_create_pkg test_pkg std_msgs rospy roscpp
    (编译工作包)
    cd ..
    catkin_make
    source devel/setup.bash
### ros编译.zip工作包
    unzip 2020RC-main.zip
    https://blog.csdn.net/weixinhum/article/details/83026236
    source ~/RC_record/ROS/devel/setup.bash
    roslaunch main program.launch
## 在ROS使用RealSense SR300相机
    - https://github.com/IntelRealSense/realsense-ros
    export ROS_VER=melodic 
    sudo apt-get install ros-$ROS_VER-realsense2-camera
    sudo apt-get install ros-$ROS_VER-realsense2-description

## tensorRt配置
### 列一下版本号

    Ubuntu 18.04
    Cuda：10.2
    Cudnn：8.0.3
    TensorRT：7.1.3.4
### 配置过程
    （https://blog.csdn.net/qq_19707521/article/details/105413411?utm_medium=distribute.pc_aggpage_search_result.none-task-blog-2~all~sobaiduend~default-1-105413411.nonecase&utm_term=ubuntu%20%E9%85%8D%E7%BD%AEtensorrt%E7%8E%AF%E5%A2%83&spm=1000.2123.3001.4430）
    -  解压tar包
        tar -zxvf  TensorRT-7.1.3.4.Ubuntu-18.04.x86_64-gnu.cuda-10.2.cudnn8.0.tar.gz
    - 环境变量设置
        gedit ~/.bashrc
        export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/media/dohbless/R/TensorRT-7.1.3.4/lib
        export TENSORRT_ROOT=/media/dohbless/R/TensorRT-7.1.3.4
        source ~/.bashrc
    - 安装TensorRT的python接口
        cd TensorRT-7.x.x.x/python
        pip install tensorrt-7.1.3.4-cp36-none-linux_x86_64.whl
     - 安装UFF（Tensorflow所使用的）
        cd TensorRT-7.x.x.x/uff
        pip install uff-0.6.9-py2.py3-none-any.whl
     - 安装graphsurgeon
        cd TensorRT-7.x.x.x/graphsurgeon
        pip install graphsurgeon-0.4.1-py2.py3-none-any.whl
        (https://blog.csdn.net/zong596568821xp/article/details/86077553?utm_medium=distribute.pc_relevant.none-task-blog-utm_term-7&spm=1001.2101.3001.4242)
    
## 重新安装opencv4
    https://blog.csdn.net/weixin_41921520/article/details/97927633

