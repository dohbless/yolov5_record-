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
