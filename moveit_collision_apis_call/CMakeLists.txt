cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(moveit_collision_apis_call)

#SET(CMAKE_BUILD_TYPE "Debug")
SET(CMAKE_BUILD_TYPE "Debug")

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++14)#(-std=c++11)#

# Eigen 3
find_package(Eigen3 REQUIRED)
include_directories(${EIGEN3_INCLUDE_DIRS})


find_package(catkin REQUIRED COMPONENTS
  roscpp
  moveit_ros_planning_interface
  moveit_core
  moveit_ros_planning
  geometric_shapes
)


include_directories(
  ${catkin_INCLUDE_DIRS}
)


catkin_package(
  CATKIN_DEPENDS
)

include_directories()


### Add library and executable
add_library(collision_checking_yumi src/collision_checking_yumi.cpp)
target_link_libraries(collision_checking_yumi ${catkin_LIBRARIES} ${Boost_LIBRARIES})

#add_executable(TEST_collision_checking_yumi src/collision_checking_yumi.cpp)
#target_link_libraries(TEST_collision_checking_yumi ${catkin_LIBRARIES} collision_checking_yumi)

