cmake_minimum_required (VERSION 3.1.0)
project(RayTracing_work_06)

set(CMAKE_CXX_STANDARD 17)

add_executable(RayTracing_work_06 main.cpp Object.hpp Vector.cpp Vector.hpp Sphere.hpp global.hpp Triangle.hpp Scene.cpp
        Scene.hpp Light.hpp AreaLight.hpp BVH.cpp BVH.hpp Bounds3.hpp Ray.hpp Material.hpp Intersection.hpp
        Renderer.cpp Renderer.hpp)
