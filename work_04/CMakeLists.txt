cmake_minimum_required (VERSION 3.1.0)
project(BezierCurve)

set(CMAKE_CXX_STANDARD 14)

include_directories(${EIGEN3_INCLUDE_DIR}
                    ${OPENCV_INCLUDE_DIR})
link_directories(${OPENCV_LIB_DIR})

add_executable(BezierCurve_work_04 main.cpp)

if(CMAKE_BUILD_TYPE AND (CMAKE_BUILD_TYPE STREQUAL "Debug"))
    target_link_libraries(BezierCurve_work_04 opencv_world343d.lib)
else()
    target_link_libraries(BezierCurve_work_04 opencv_world343.lib)
endif()