cmake_minimum_required(VERSION 2.8.3)
project(tutorial)
find_package(catkin REQUIRED COMPONENTS message_generation std_msgs rospy roscpp)

add_service_files(FILES prime_request.srv)
generate_messages(DEPENDENCIES std_msgs)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs roscpp
)

catkin_install_python(PROGRAMS scripts/py
	DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

add_executable(cpp src/cpp.cpp)
target_link_libraries(cpp ${catkin_LIBRARIES})
add_dependencies(cpp tutorial_gencpp)
