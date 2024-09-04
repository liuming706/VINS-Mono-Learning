# VIO
## prepare
```bash
sudo apt install libceres-dev 
```
##  L515 运行 VINS-Mono

```bash
# 方式 1
roslaunch realsense2_camera rs_camera.launch \
    align_depth:=true \
    unite_imu_method:="copy" \
    enable_gyro:=true \
    enable_accel:=true \
    enable_sync:=true
# 方式 2
roslaunch realsense2_camera rs_camera.launch     align_depth:=true     unite_imu_method:="linear_interpolation"     enable_gyro:=true     enable_accel:=true     enable_sync:=true
    
roslaunch vins_estimator realsense_color.launch 
roslaunch vins_estimator vins_rviz.launch # 或者直接打开 rviz ，add path 话题，global_option 选择 world
```
##  数据集运行 VINS-Mono
[下载 MH_01_easy.bag](http://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets)
```bash
source devel/setup.bash && roslaunch vins_estimator euroc.launch 
source devel/setup.bash && roslaunch vins_estimator vins_rviz.launch
source devel/setup.bash && rosbag play ~/workspace/datasets//MH_01_easy.bag 
```