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
- 配置环境变量 export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64
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
 
 ## pip 安装pytorch
 pip install torch==1.6.0+cu101 torchvision==0.7.0+cu101 -i  https://pypi.tuna.tsinghua.edu.cn/simple
  pip install torch==1.6.0+cu101 torchvision==0.7.0+cu101 -i http://pypi.douban.com/simple/
  
  https://download.pytorch.org/whl/torch_stable.html
  
  pip --default-timeout=100 install torch torchvision -i  https://pypi.tuna.tsinghua.edu.cn/simple
https://blog.csdn.net/qq_15192373/article/details/104244743 简单直白

## realsense相机驱动安装

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
