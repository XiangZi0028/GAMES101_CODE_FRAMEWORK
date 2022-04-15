cmake_minimum_required (VERSION 3.1.0)
project(Rasterizer_work_02)
set(CMAKE_CXX_STANDARD 17)

if (NOT T_LIBRARY_OUTPUT_PATH)
    set(T_LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/Bin)
endif ()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})



include_directories(${OPENCV_INCLUDE_DIR})
include_directories(${EIGEN3_INCLUDE_DIR})
link_directories(${OPENCV_LIB_DIR})
add_executable(Rasterizer_work_02 main.cpp rasterizer.hpp rasterizer.cpp global.hpp Triangle.hpp Triangle.cpp)
if(CMAKE_BUILD_TYPE AND (CMAKE_BUILD_TYPE STREQUAL "Debug"))
    target_link_libraries(Rasterizer_work_02 opencv_world343d.lib)
else()
    target_link_libraries(Rasterizer_work_02 opencv_world343.lib)
endif()
