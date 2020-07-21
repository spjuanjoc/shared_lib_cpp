cmake_minimum_required(VERSION 3.10)

project(shared_lib_cpp VERSION 0.0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

include_directories(include)

set(SOURCES
  src/library.cpp
  src/Foo.cpp
)

# Create shared library target
add_library(${PROJECT_NAME} SHARED ${SOURCES})

# Create static library target
#add_library(${PROJECT_NAME} STATIC ${SOURCES})

# Define target properties
target_include_directories(${PROJECT_NAME}
  PUBLIC
  $<INSTALL_INTERFACE:include>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#  PRIVATE
#  ${CMAKE_CURRENT_SOURCE_DIR}/src # if headers here
)
