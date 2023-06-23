cmake_minimum_required(VERSION 3.22)
project(stb_image)

option(STB_IMAGE_LOAD  "Compile stb_image"       ON)
option(STB_IMAGE_WRITE "Compile stb_image_write" ON)
option(STB_TRUETYPE    "Compile stb_truetype"    ON)

configure_file(stb_impl.cpp.in ${CMAKE_BINARY_DIR}/stb_impl.cpp)

include_directories(${CMAKE_SOURCE_DIR})

add_library(stb STATIC ${CMAKE_BINARY_DIR}/stb_impl.cpp)


# install
install(
  TARGETS stb
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib)

install(
  DIRECTORY ${CMAKE_SOURCE_DIR}/
  DESTINATION include/stb
  FILES_MATCHING
  PATTERN "*.h"
  PATTERN ".git" EXCLUDE)
