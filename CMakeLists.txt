cmake_minimum_required(VERSION 3.12)
project(sofabounds)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_CXX_FLAGS "-O3 -Wfatal-errors -Wno-switch -DCMAKE_CXX_FLAGS='-DCGAL_USE_BOOST_MP'")

set(CMAKE_BUILD_TYPE "Release")

set(SOURCES
    sofa-bounds.cpp
    branch-and-bound.cpp
    frontend.cpp
    )
    
# set(CGAL_USE_GMP false)
# set(CGAL_DISABLE_GMP true)

# CGAL and its components
find_package( CGAL QUIET COMPONENTS  )
if ( NOT CGAL_FOUND )
  message(STATUS "This project requires the CGAL library, and will not be compiled.")
  return()
endif()

# Boost and its components
find_package( Boost REQUIRED )
if ( NOT Boost_FOUND )
  message(STATUS "This project requires the Boost library, and will not be compiled.")
  return()
endif()


# find_package(CGAL "5.0")
# find_package(Boost "1.7")


add_executable(sofabounds ${SOURCES})
target_link_libraries(sofabounds LINK_PUBLIC ${CGAL_LIBRARIES} )
target_link_libraries(sofabounds LINK_PUBLIC ${Boost_LIBRARIES} )
# target_link_libraries(sofabounds LINK_PUBLIC . )
target_include_directories(sofabounds PUBLIC .)
