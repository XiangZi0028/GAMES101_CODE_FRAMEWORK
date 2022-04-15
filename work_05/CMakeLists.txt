cmake_minimum_required (VERSION 3.1.0)
project(RayTracing_work_05)

set(CMAKE_CXX_STANDARD 17)

add_executable(RayTracing_work_05 main.cpp Object.hpp Vector.hpp Sphere.hpp global.hpp Triangle.hpp Scene.cpp Scene.hpp Light.hpp Renderer.cpp)
#target_compile_options(RayTracing PUBLIC -Wall  -pedantic -Wshadow -Wreturn-type -fsanitize=undefined)
#target_compile_features(RayTracing PUBLIC cxx_std_17)
target_link_libraries(RayTracing_work_05 PUBLIC -fsanitize=undefined)
