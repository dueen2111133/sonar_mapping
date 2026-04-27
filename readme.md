
将ros2录制的声纳图像与lio对齐
python3 /home/siyuan/bluerov_ws/src/sonar_mapping/script/align_odom_to_sonar.py
查看声纳图像像素
python3 /home/siyuan/bluerov_ws/src/sonar_mapping/script/click_ros_pic.py
建立地图效果对比
python /home/siyuan/bluerov_ws/src/sonar_mapping/script/map_compair.py



编译
colcon build --packages-select sonar_mapping
colcon build --packages-select sonar_mapping --cmake-args -DCMAKE_BUILD_TYPE=Release
MAKEFLAGS="-j1" colcon build --packages-select sonar_mapping --cmake-args -DCMAKE_BUILD_TYPE=Release

工作空间加入系统
source /home/siyuan/sonar_ws/install/setup.bash


单独测试图片处理效果
ros2 run sonar_mapping cfar_real_test

ros线程处理声纳图片
ros2 run sonar_mapping cfar_ros_node

矫正的sonar建图
ros2 run sonar_mapping sonar_mapping_node
没有矫正的sonar建图
ros2 run sonar_mapping sonar_mapping_sync_node
声纳建图输出时间
ros2 run sonar_mapping sonar_mapping_node_realtime
lidar建图
ros2 run sonar_mapping sonar_mapping_node





# 播放数据包
cd /home/siyuan/sonar_slam/data/lio_sonar/combine
ros2 bag play record_404_15_09_5hz --start-offset 5
ros2 bag play record_404_10_35_5hz --start-offset 4
