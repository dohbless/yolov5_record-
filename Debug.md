## opencv4
    $ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
    $ make -j6 	# runs 6 jobs in parallel
    
    PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
    export PKG_CONFIG_PATH
   
    $ pkg-config --libs opencv4
-L/usr/local/lib -lopencv_ml -lopencv_dnn -lopencv_video -lopencv_stitching -lopencv_objdetect -lopencv_calib3d -lopencv_features2d -lopencv_highgui -lopencv_videoio -lopencv_imgcodecs -lopencv_flann -lopencv_photo -lopencv_gapi -lopencv_imgproc -lopencv_core


 locate opencv.pc
 /usr/lib/x86_64-linux-gnu/pkgconfig/opencv.pc
 
  sudo vim /etc/profile.d/pkgconfig.sh


