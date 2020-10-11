cmake_minimum_required(VERSION 3.10)

project(shared_lib_cpp VERSION 0.0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

option(ENABLE_TESTS "Enable tests" OFF)

include_directories(include)

set(SOURCES
    src/Library.cpp
  src/Foo.cpp
)

# Create shared library target
add_library(${PROJECT_NAME} SHARED ${SOURCES})

# Create static library target
#add_library(${PROJECT_NAME} STATIC ${SOURCES})

# --
# --
# target instructions must be after add_executable or add_library instructions

# Get the headers
set(INCLUDES include)
include_directories(PUBLIC ${INCLUDES})
target_include_directories(${PROJECT_NAME} PUBLIC ${INCLUDES})


# Define target properties
target_include_directories(${PROJECT_NAME}
  PUBLIC
  $<INSTALL_INTERFACE:include>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#  PRIVATE
#  ${CMAKE_CURRENT_SOURCE_DIR}/src # if headers here
)

if(ENABLE_TESTS)
  enable_testing()
  add_subdirectory(test)
elseif()
  message("Tests not included")
endif()

# Install instructions
