cmake_minimum_required(VERSION 3.0.2)
project(rl_tiago)

find_package(catkin REQUIRED COMPONENTS
  #roscpp
  rospy
  std_msgs
  gazebo_msgs
  geometry_msgs
  nav_msgs
)

catkin_python_setup()

catkin_package(
  CATKIN_DEPENDS gazebo_msgs geometry_msgs nav_msgs
)

include_directories(SYSTEM ${catkin_INCLUDE_DIRS})

foreach(dir launch worlds)
    install(DIRECTORY ${dir}/
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

install(PROGRAMS scripts/tuck_arm.py
        DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
