cmake_minimum_required (VERSION 3.1.0)
project(Rasterizer_work_03)

set(CMAKE_CXX_STANDARD 17)

include_directories(${EIGEN3_INCLUDE_DIR}
                    ${OPENCV_INCLUDE_DIR})
link_directories(${OPENCV_LIB_DIR})
add_executable(Rasterizer_work_03 main.cpp rasterizer.hpp rasterizer.cpp global.hpp Triangle.hpp Triangle.cpp Texture.hpp Texture.cpp Shader.hpp OBJ_Loader.h)
if(CMAKE_BUILD_TYPE AND (CMAKE_BUILD_TYPE STREQUAL "Debug"))
    target_link_libraries(Rasterizer_work_03 opencv_world343d.lib)
else()
    target_link_libraries(Rasterizer_work_03 opencv_world343.lib)
endif()