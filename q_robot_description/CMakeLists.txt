cmake_minimum_required(VERSION 2.8.3)

project(q_robot_description)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  robot_state_publisher
  joint_state_publisher
  joint_state_publisher_gui
  urdf
  xacro
)

## Declare a catkin package
catkin_package()

## Install all necessary files
foreach(dir config launch meshes urdf)
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir}
  )
endforeach(dir)

## Test xacro files (optional but helpful during debugging)
find_package(roslaunch REQUIRED)
roslaunch_add_file_check(launch)
