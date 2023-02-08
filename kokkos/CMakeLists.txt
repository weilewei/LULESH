cmake_minimum_required(VERSION 3.20.3)
project(parSTL LANGUAGES CXX C)

set(CMAKE_BUILD_TYPE Release)

set(Kokkos_DIR "/global/homes/w/wwei/install/kokkos_cpu/lib64/cmake/Kokkos/")
find_package(Kokkos REQUIRED)

if (KOKKOS_FOUND)
  include_directories(${KOKKOS_INCLUDE_DIRS})
endif()

add_definitions(-DUSE_MPI=0) 

add_executable(kokkosPar     
lulesh.cc 
lulesh-comm.cc 
lulesh-viz.cc 
lulesh-util.cc 
lulesh-init.cc)
target_link_libraries(kokkosPar Kokkos::kokkos)
target_include_directories(kokkosPar PRIVATE "${CMAKE_CURRENT_LIST_DIR}/include" "${CMAKE_CURRENT_LIST_DIR}")    
