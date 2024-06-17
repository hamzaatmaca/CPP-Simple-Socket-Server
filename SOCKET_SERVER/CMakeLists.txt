# CMake minimum version requirement
cmake_minimum_required(VERSION 3.10)

# Project name and version
project(CPP VERSION 1.0)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add include directories
include_directories(${CMAKE_SOURCE_DIR}/include)

# Specify the source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

# Set the output directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/dist)

# Add the executable
add_executable(socketserver ${SOURCES})

# Custom target to run the executable
add_custom_target(run
    COMMAND ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/socketserver
    DEPENDS socketserver
    WORKING_DIRECTORY ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}
    COMMENT "Running the socketserver executable"
)
