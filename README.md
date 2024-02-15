## Robot Package Template

This is a GitHub template. You can make your own copy by clicking the green "Use this template" button.

It is recommended that you keep the repo/package name the same, but if you do change it, ensure you do a "Find all" using your IDE (or the built-in GitHub IDE by hitting the `.` key) and rename all instances of `my_bot` to whatever your project's name is.

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).

## Steps to execute my_bot on hardware-
- ros2 launch my_bot robot_launch.launch.py 
- ros2 launch rplidar_ros rplidar_a1_launch.py frame_id:=laser_frame
(To fake `odom` use the following else publish from hardware)
- ros2 run tf2_ros static_transform_publisher 0 0 0 0 0 0 base_link odom
- ros2 topic pub /odom nav_msgs/msg/Odometry "header:
  stamp:
    sec: 0
    nanosec: 0
  frame_id: 'odom'
child_frame_id: 'base_link'
pose:
  pose:
    position:
      x: 0.0
      y: 0.0
      z: 0.0
    orientation:
      x: 0.0
      y: 0.0
      z: 0.0
      w: 1.0
.
.
.
.
"
