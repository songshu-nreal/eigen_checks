cmake_minimum_required(VERSION 2.8.3)
project(eigen_checks)

find_package(catkin_simple REQUIRED)
catkin_simple()

add_definitions(--std=c++0x -Wall -Wextra -pedantic)

cs_add_library(${PROJECT_NAME} src/eigen_checks.cc)

catkin_add_gtest(test_gtest_near
	test/test_gtest_near.cc)
target_link_libraries(test_gtest_near ${PROJECT_NAME})

catkin_add_gtest(test_gtest_equal
  test/test_gtest_equal.cc)
target_link_libraries(test_gtest_equal ${PROJECT_NAME})

catkin_add_gtest(test_gtest_equal_double
  test/test_gtest_equal_double.cc)
target_link_libraries(test_gtest_equal_double ${PROJECT_NAME})

catkin_add_gtest(test_glog_near
  test/test_glog_near.cc)
target_link_libraries(test_glog_near ${PROJECT_NAME})

catkin_add_gtest(test_glog_equal
  test/test_glog_equal.cc)
target_link_libraries(test_glog_equal ${PROJECT_NAME})

catkin_add_gtest(test_glog_equal_double
  test/test_glog_equal_double.cc)
target_link_libraries(test_glog_equal_double ${PROJECT_NAME})

cs_install()

cs_export(INCLUDE_DIRS include
          CFG_EXTRAS eigen_checks-extras.cmake)