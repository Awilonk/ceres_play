cmake_minimum_required(VERSION 3.0.2)
project(ceres_play)

set(CMAKE_CXX_FLAGS "-std=c++14")
set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall -fPIC")

find_package(Eigen3 REQUIRED)
find_package(ompl REQUIRED)
find_package(Ceres REQUIRED)


find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  geometry_msgs
  sensor_msgs
  visualization_msgs
)

include_directories(
    ${catkin_INCLUDE_DIRS}
    ${OMPL_INCLUDE_DIRS}
    ${EIGEN3_INCLUDE_DIRS}
    include
)

catkin_package()

add_executable(ceres_play_node src/simple_test_node.cpp)

target_link_libraries(ceres_play_node
  ${CERES_LIBRARIES}
  ${OMPL_LIBRARIES}
  ${catkin_LIBRARIES}
)
