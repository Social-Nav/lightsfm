cmake_minimum_required(VERSION 3.8)
project(lightsfm)

# Header-only: no library to compile, only headers to export.
find_package(ament_cmake REQUIRED)

# Consumers write `#include <lightsfm/sfm.hpp>`, but upstream keeps the headers
# flat in include/ -- the `lightsfm/` component only ever existed because the
# Makefile's install target created it (`cp include/* /usr/local/include/lightsfm`).
# Reproduce that layout in the install space so the include path consumers
# already use keeps working unchanged.
install(
  DIRECTORY include/
  DESTINATION include/lightsfm
  FILES_MATCHING PATTERN "*.hpp"
)

# Export include/ (not include/lightsfm/) so the `lightsfm/` prefix in consumers'
# include directives resolves against it.
ament_export_include_directories(include)

ament_package()
