cmake_minimum_required(VERSION 3.8)
project(dua_geometry_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(dua_common_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(SRV_DIR "${CMAKE_CURRENT_SOURCE_DIR}/srv")
file(GLOB SRV_FILES RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "${SRV_DIR}/*.srv")

rosidl_generate_interfaces(${PROJECT_NAME}
  ${SRV_FILES}
  DEPENDENCIES builtin_interfaces dua_common_interfaces geometry_msgs)

ament_export_dependencies(
  builtin_interfaces
  dua_common_interfaces
  geometry_msgs)

ament_package()
