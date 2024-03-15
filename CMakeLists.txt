cmake_minimum_required(VERSION 3.5.0)
project(glfw_playground)

include(CTest)
enable_testing()

find_package(OpenGL REQUIRED)
set(OpenGL_GL_PREFERENCE GLVND)

add_subdirectory(vendor/glfw)


add_executable(${PROJECT_NAME} main.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC vendor/glfw/include)
target_include_directories(${PROJECT_NAME} PRIVATE vendor/glfw/src)

target_link_libraries(${PROJECT_NAME} glfw OpenGL::GL)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
