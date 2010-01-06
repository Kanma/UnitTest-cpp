cmake_minimum_required(VERSION 2.6)
project(UNITTEST_CPP)

# Options
if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

# Set the output path
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${UNITTEST_CPP_BINARY_DIR}/lib")

# Subdirectories
add_subdirectory(src)