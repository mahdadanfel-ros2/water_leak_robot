cmake_minimum_required(VERSION 3.8)
project(water_leak_robot)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)

ament_python_install_package(${PROJECT_NAME})

install(PROGRAMS
  scripts/humidity_sensor_node.py
  scripts/leak_detector_node.py
  scripts/alert_manager_node.py
  scripts/detection_logger.py
  scripts/simple_waypoint_follower.py
  scripts/zone_coverage_node.py
  DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY
  urdf
  meshes
  worlds
  config
  launch
  DESTINATION share/${PROJECT_NAME}
)

ament_package()
