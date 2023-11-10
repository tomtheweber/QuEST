# author: Ania Brown 
# author: Jacob Wilkins
# author: Balint Koczor (Windows compatibility)
# author: Tyson Jones (testing)

# CMake initialisation.
cmake_minimum_required(VERSION 3.7)

message(STATUS "CMake version: ${CMAKE_VERSION}")
message(STATUS "CMake build type: ${CMAKE_BUILD_TYPE}")

# Project name
project(QuEST_Project)

# -----------------------------------------------------------------------------
# ----- QuEST LIBRARY ---------------------------------------------------------
# ----------------------------------------------------------------------------- 

# Build the QuEST library if the path to libQuEST.so is not specified
if (NOT DEFINED ${QuEST_LIB_PATH})
    # Build libQuEST.so
    set(QuEST_DIR "QuEST" CACHE STRING 
        "Name of the directory containing the QuEST library sources. It must be located in the same directory as the root CMakeLists.txt")
    add_subdirectory(${QuEST_DIR})
    set(QuEST_LIB_PATH "${CMAKE_CURRENT_BINARY_DIR}/${QuEST_DIR}")
    set(QuEST_LIB_EXACT "${QuEST_LIB_PATH}/libQuEST.so")
endif()
