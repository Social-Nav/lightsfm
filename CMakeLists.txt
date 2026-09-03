cmake_minimum_required(VERSION 3.8)
project(lightsfm)

find_package(ament_cmake REQUIRED)

# Headers are flat in include/; consumers write <lightsfm/sfm.hpp>, so install
# them one level down and export include/ as the search root.
install(
  DIRECTORY include/
  DESTINATION include/lightsfm
  FILES_MATCHING PATTERN "*.hpp"
)
ament_export_include_directories(include)

ament_package()
