cmake_minimum_required(VERSION 3.8)
project(get_object_pose_action_client)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(grasping_msgs REQUIRED)

# add executables and dependencies
add_executable(get_object_pose_action_client 
  src/get_object_pose_action_client.cpp)
target_include_directories(get_object_pose_action_client 
  PUBLIC include)
ament_target_dependencies(get_object_pose_action_client 
  rclcpp 
  rclcpp_action 
  std_msgs 
  geometry_msgs 
  grasping_msgs)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# install the executables
install(TARGETS
   get_object_pose_action_client
   DESTINATION lib/${PROJECT_NAME}
 )

# install the launch files
install(DIRECTORY
  launch
  DESTINATION share/${PROJECT_NAME}/
)

ament_package()