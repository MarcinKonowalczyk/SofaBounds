cmake_minimum_required(VERSION 3.12)
project(sofabounds)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_CXX_FLAGS "-O3 -pedantic -Wall -Wfatal-errors")
set(CMAKE_BUILD_TYPE "Release")

set(SOURCES
    sofa-bounds.cpp
    branch-and-bound.cpp
    frontend.cpp
    )

find_package(CGAL REQUIRED)
add_executable(sofabounds ${SOURCES})
target_link_libraries(sofabounds LINK_PUBLIC ${CGAL_LIBRARIES} )
target_include_directories(sofabounds PUBLIC .)
