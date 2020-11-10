## opencv4
    $ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
    $ make -j6 	# runs 6 jobs in parallel
    
    PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
    export PKG_CONFIG_PATH
   
    $ pkg-config --libs opencv4 -L/usr/local/lib -lopencv_ml -lopencv_dnn -lopencv_video -lopencv_stitching -lopencv_objdetect -lopencv_calib3d -lopencv_features2d -lopencv_highgui -lopencv_videoio -lopencv_imgcodecs -lopencv_flann -lopencv_photo -lopencv_gapi -lopencv_imgproc -lopencv_core


 locate opencv.pc
 /usr/lib/x86_64-linux-gnu/pkgconfig/opencv.pc
 
  export PKG_CONFIG_PATH=/usr/lib/x86_64-linux-gnu/pkgconfig/:$PKG_CONFIG_PATH

 opencv-4.1.2/sample/cpp/example_cmake 
 
 NvInfer.h
 
 export DSO_PATH=~/.local/share/Trash/files/TensorRT-7.1.3.4/include

sudo apt-get install aptitude

暴力包含头文件
https://blog.csdn.net/w383117613/article/details/46049273?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param
https://blog.csdn.net/best3c/article/details/72848803

cp -v /home/dohbless/.local/share/Trash/files/TensorRT-7.1.3.4/include/NvInferRuntime.h /home/dohbless/hello_rc/src/neural_net/include/neural_net

sudo cp -v /home/dohbless/.local/share/Trash/files/cuda.2/include/cudnn_backend.h /usr/local/cuda-10.2/include
找不到连接
https://www.cnblogs.com/feifanrensheng/p/10039959.html
sudo cp /usr/local/cuda-10.2/targets/x86_64-linux/lib/libcudart.so  /usr/local/lib/
注册环境变量
source devel/setup.bash
使用roslaunch
roslaunch main pro

包含动态连接库
sudo cp -v /home/dohbless/.local/share/Trash/files/TensorRT-7.1.3.4/targets/x86_64-linux-gnu/lib/libmyelin.so.1 /usr/local/lib/



