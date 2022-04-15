cmake_minimum_required(VERSION 3.20)

if (NOT T_LIBRARY_OUTPUT_PATH)
    set(T_LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/Bin)
endif ()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${T_LIBRARY_OUTPUT_PATH})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELWITHDEBINFO ${T_LIBRARY_OUTPUT_PATH})

# Application source
set(APPLICATION_SOURCE
    rope.cpp
    application.cpp
    main.cpp
)

#-------------------------------------------------------------------------------
# Set include directories
#-------------------------------------------------------------------------------
include_directories(
  ${FREETYPE_INCLUDE_DIR}
  ${GLEW_INCLUDE_DIRS}
  ${GLFW_INCLUDE_DIRS}
  ${CGL_INCLUDE_DIRS}
)

#-------------------------------------------------------------------------------
# Set link directories
#-------------------------------------------------------------------------------
set(FREETYPE_LIBRARY_DIR ${CMAKE_BINARY_DIR}/Bin)
set(CGL_LIBRARY_DIRS ${CMAKE_BINARY_DIR}/Bin)
link_directories(
  ${GLEW_LIBRARY_DIRS}
  ${GLFW_LIBRARY_DIRS}
  ${CGL_LIBRARY_DIRS}
  ${FREETYPE_LIBRARY_DIR}
)

#-------------------------------------------------------------------------------
# Add executable
#-------------------------------------------------------------------------------
add_executable(ropesim ${APPLICATION_SOURCE})

target_link_libraries( ropesim
    CGL ${CGL_LIBRARIES}
    glew ${GLEW_LIBRARIES}
    glfw ${GLFW_LIBRARIES}
    ${OPENGL_LIBRARIES}
    freetyped.lib
    ${CMAKE_THREADS_INIT}
)

#-------------------------------------------------------------------------------
# Platform-specific configurations for target
#-------------------------------------------------------------------------------
if(APPLE)
  set_property( TARGET ropesim APPEND_STRING PROPERTY COMPILE_FLAGS
                "-Wno-deprecated-declarations -Wno-c++11-extensions")
endif(APPLE)

# Put executable in build directory root
# Install to project root
#install(TARGETS ropesim DESTINATION ${RopeSim_SOURCE_DIR})
