cmake_minimum_required(VERSION 3.8)
project(tmc_manipulation_msgs)

if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(moveit_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/BaseMovementType.msg"
  "msg/IkResult.msg"
  "srv/FilterJointTrajectory.srv"
  "srv/SolveIkWithCollision.srv"
  DEPENDENCIES builtin_interfaces geometry_msgs moveit_msgs nav_msgs sensor_msgs trajectory_msgs
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
