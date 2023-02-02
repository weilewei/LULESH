cmake_minimum_required(VERSION 3.20.3)
project(parSTL LANGUAGES CXX C)

set(CMAKE_BUILD_TYPE Debug)

set(HPX_DIR "/global/homes/w/wwei/install/hpx_Release/lib64/cmake/HPX/")

find_package(HPX REQUIRED)

if (HPX_FOUND)
  include_directories(${HPX_INCLUDE_DIRS})
endif()

add_definitions(-DUSE_MPI=0) 

# add_executable(hpxPar lulesh.cc 
# lulesh-comm.cc 
# lulesh-viz.cc 
# lulesh-util.cc 
# lulesh-init.cc)
# target_link_libraries(hpxPar PUBLIC HPX::hpx HPX::wrap_main HPX::iostreams_component)


add_hpx_executable(hpxPar
    ESSENTIAL
    SOURCES 
    lulesh.cc 
    lulesh-comm.cc 
    lulesh-viz.cc 
    lulesh-util.cc 
    lulesh-init.cc
    HEADERS
    lulesh.h
)