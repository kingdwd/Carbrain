cmake_minimum_required(VERSION 2.8.3)
project(controller_msgs)

find_package(catkin REQUIRED COMPONENTS message_generation std_msgs geometry_msgs sensor_msgs)
# We want boost/format.hpp, which isn't in its own component.
find_package(Boost REQUIRED)

find_package(kitcar_cmake)
add_files_to_project()

add_message_files(
  DIRECTORY msg
  FILES StateMeasure.msg WheelSpeeds.msg SteeringAngles.msg VectorLR.msg BlinkerCommand.msg LightsCommand.msg)

generate_messages(DEPENDENCIES std_msgs geometry_msgs sensor_msgs)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs geometry_msgs sensor_msgs
  DEPENDS Boost)
