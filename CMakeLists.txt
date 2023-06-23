cmake_minimum_required(VERSION 3.25)
project(stb_image)

option(STBI_LOAD  "Compile stb_image"       ON)
option(STBI_WRITE "Compile stb_image_write" ON)

if (STBI_LOAD)
	add_definitions(-DSTBI_LOAD)
endif()

if (STBI_WRITE)
	add_definitions(-DSTBI_WRITE)
endif()

add_library(stb_image STATIC stb_image.cpp stb_image.h stb_image_write.h)


# install
install(
  TARGETS stb_image
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib)

install(
  DIRECTORY ${CMAKE_SOURCE_DIR}/
  DESTINATION include/stb
  FILES_MATCHING
  PATTERN "*.h"
  PATTERN ".git" EXCLUDE)
