cmake_minimum_required (VERSION 3.1.0)
project(GAMES101)

if (NOT T_LIBRARY_OUTPUT_PATH)
    set(T_LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/Bin)
endif ()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})



set(OPENCV_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3party/opencv/build/include CACHE INTERNAL "opencv_include_dir")
set(OPENCV_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3party/opencv/build/x64/vc15/lib CACHE INTERNAL "opencv_lib_dir")
set(EIGEN3_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3party CACHE INTERNAL "eigen3_include_dir")
set(FREEYYPE_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3party/freetype-2.12.0/include CACHE INTERNAL "freetype_include_dir")
set(OPENCV_DLL_RELEASE ${CMAKE_CURRENT_SOURCE_DIR}/3party/opencv/build/x64/vc15/bin/opencv_world343.dll CACHE INTERNAL "opencv_dlls opencv_world343.dll  Release ")
set(OPENCV_DLL_DEBUG ${CMAKE_CURRENT_SOURCE_DIR}/3party/opencv/build/x64/vc15/bin/opencv_world343d.dll CACHE INTERNAL "opencv_dlls opencv_world343.dll  Debug ")

# 拷贝文件夹到指定的目录
message("####################${CMAKE_SOURCE_DIR}")
add_custom_target(COPY ALL)
add_custom_command(TARGET COPY
PRE_BUILD
COMMAND ${CMAKE_COMMAND} -E copy_directory  
"${CMAKE_SOURCE_DIR}/models"
"${T_LIBRARY_OUTPUT_PATH}/models"
COMMAND ${CMAKE_COMMAND} -E copy 
"${OPENCV_DLL_DEBUG}"
"${T_LIBRARY_OUTPUT_PATH}"
COMMAND ${CMAKE_COMMAND} -E copy 
"${OPENCV_DLL_RELEASE}"
"${T_LIBRARY_OUTPUT_PATH}"
)

add_subdirectory(3party)

add_subdirectory(work_00)
#  add_subdirectory(work_01)
add_subdirectory(work_02)
add_subdirectory(work_03)
add_subdirectory(work_04)
add_subdirectory(work_05)
add_subdirectory(work_06)
add_subdirectory(work_07)