cmake_minimum_required(VERSION 3.1)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/lsolanka/hunter/archive/v0.22.4-rosdevel19.tar.gz"
    SHA1 "06122fac73b2ee45aeff597e49eaaf3cfebdc330"
)

project(mrpt_msgs)

hunter_add_package(catkin)
hunter_add_package(ros_message_generation)
hunter_add_package(ros_message_runtime)
hunter_add_package(ros_std_msgs)
hunter_add_package(ros_common_msgs)

find_package(catkin REQUIRED COMPONENTS
    geometry_msgs
    message_generation
    sensor_msgs
    std_msgs
    )

add_message_files(
  DIRECTORY msg
  FILES
  GraphConstraint.msg
  GraphSlamAgent.msg
  GraphSlamAgents.msg
  GraphSlamStats.msg
  NetworkOfPoses.msg
  NodeIDWithLaserScan.msg
  NodeIDWithPose_vec.msg
  NodeIDWithPose.msg
  ObservationRangeBeacon.msg
  ObservationRangeBearing.msg
  SingleRangeBeaconObservation.msg
  SingleRangeBearingObservation.msg
  )


add_service_files(
   DIRECTORY srv
   FILES
   GetCMGraph.srv
   )

generate_messages(DEPENDENCIES
    geometry_msgs
    sensor_msgs
    std_msgs
	)

catkin_package(CATKIN_DEPENDS
    geometry_msgs
    message_runtime
    sensor_msgs
    std_msgs
	)
