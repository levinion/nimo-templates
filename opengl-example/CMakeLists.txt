set(name "opengl-example")
cmake_minimum_required(VERSION 3.10)
project(${name} CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(./third_party/glfw-3.4)
add_subdirectory(./third_party/glad)

add_executable(${name} "main.cpp")
target_link_options(${name} PRIVATE -static-libgcc -static-libstdc++)

target_link_libraries(${name} glfw)
target_link_libraries(${name} glad)

find_package(OpenGL REQUIRED)
target_link_libraries(${name} OpenGL::GL)
