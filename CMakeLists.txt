cmake_minimum_required(VERSION 2.6)
project(UNITTEST_CPP)

# Options
if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

# Set the output path
if (NOT CMAKE_ARCHIVE_OUTPUT_DIRECTORY)
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${UNITTEST_CPP_BINARY_DIR}/lib")
endif()

# XMake settings
if (EXISTS "${UNITTEST_CPP_SOURCE_DIR}/dependencies/xmake/XMake.cmake")
    include("${UNITTEST_CPP_SOURCE_DIR}/dependencies/xmake/XMake.cmake")
endif()

xmake_init_static(UNITTEST_CPP)
xmake_add_include_paths(UNITTEST_CPP "${UNITTEST_CPP_SOURCE_DIR}/include")
xmake_add_link_paths(UNITTEST_CPP "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY}")
xmake_add_link_targets(UNITTEST_CPP UnitTest++)

# Subdirectories
add_subdirectory(src)
