cmake_minimum_required(VERSION 2.8.3)
project(clam_moveit_experimental)

find_package(Eigen REQUIRED)
find_package(Boost REQUIRED thread date_time system filesystem program_options python)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS 
  roscpp 
  actionlib 
  tf
  clam_block_manipulation
  eigen_conversions 
  moveit_ros_planning 
  moveit_ros_planning_interface
)

###################################################
## Declare things to be passed to other projects ##
###################################################

## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#   INCLUDE_DIRS 
#     include
   CATKIN_DEPENDS 
      roscpp 
      actionlib 
      tf
      clam_block_manipulation
      eigen_conversions 
      moveit_ros_planning 
      moveit_ros_planning_interface
#  DEPENDS system_lib
)

###########
## Build ##
###########

## Specify additional locations of header files
include_directories(
#  include
  ${catkin_INCLUDE_DIRS}
)
link_directories(${catkin_LIBRARY_DIRS})

## Declare cpp executables

# Coverage test
add_executable(coverage_test src/coverage_test.cpp)
target_link_libraries(coverage_test ${catkin_LIBRARIES})

# Gripper Test
add_executable(gripper_test src/gripper_test.cpp)
target_link_libraries(gripper_test ${catkin_LIBRARIES})

# End effector offset test
add_executable(ee_offset_test src/ee_offset_test.cpp)
target_link_libraries(ee_offset_test ${catkin_LIBRARIES})

# Up Down Test
add_executable(up_down_test src/up_down_test.cpp)
target_link_libraries(up_down_test ${catkin_LIBRARIES})


#############
## Install ##
#############

## Mark executable scripts (Python etc.) for installation
## not required for python when using catkin_python_setup()
# install(PROGRAMS
#   scripts/my_python_script
#   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## Mark executables and/or libraries for installation
# install(TARGETS clam_moveit_experimental clam_moveit_experimental_node
#   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## Mark cpp header files for installation
# install(DIRECTORY include/${PROJECT_NAME}/
#   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
#   FILES_MATCHING PATTERN "*.h"
#   PATTERN ".svn" EXCLUDE
# )

## Mark other files for installation (e.g. launch and bag files, etc.)
# install(FILES
#   # myfile1
#   # myfile2
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
# )

#############
## Testing ##
#############

## Add gtest based cpp test target and link libraries
# catkin_add_gtest(${PROJECT_NAME}-test test/test_clam_moveit_experimental.cpp)
# if(TARGET ${PROJECT_NAME}-test)
#   target_link_libraries(${PROJECT_NAME}-test ${PROJECT_NAME})
# endif()

## Add folders to be run by python nosetests
# catkin_add_nosetests(test)
