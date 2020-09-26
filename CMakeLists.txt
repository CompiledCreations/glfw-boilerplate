cmake_minimum_required(VERSION 3.0.0)
project(boilerplate VERSION 0.1.0)

include(CTest)
enable_testing()

# Build GLFW using the official method [here](https://www.glfw.org/docs/3.3/compile_guide.html#compile_cmake)
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory("dependencies/glfw")

# Compile our GLAD library. You can regenerate and drop in a version for your project [here](https://gen.glad.sh/)
add_library(glad dependencies/glad/src/gl.c)
target_include_directories(glad PUBLIC dependencies/glad/include)

# Add this to project include dirs to use linmath
set(LINMATH_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/dependencies/linmath")

# Add our subprojects here...
add_subdirectory("projects/boilerplate")

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
