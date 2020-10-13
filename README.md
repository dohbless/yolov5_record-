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
