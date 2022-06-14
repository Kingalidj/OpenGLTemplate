cmake_minimum_required(VERSION 3.10)

set(PROJ_NAME Template)
project(${PROJ_NAME})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_VERBOSE_MAKEFILE 1)
#set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

add_subdirectory(vendor/glfw)
include_directories(vendor/glfw/include)

include_directories(vendor/imgui)
include_directories(vendor/imgui/backends)


include_directories(vendor/glad/include)

set(SOURCES ${SOURCES}
    vendor/glad/src/glad.c

    vendor/imgui/imgui_demo.cpp
    vendor/imgui/imgui_draw.cpp
    vendor/imgui/imgui_tables.cpp
    vendor/imgui/imgui_widgets.cpp
    vendor/imgui/imgui.cpp

    vendor/imgui/backends/imgui_impl_opengl3.cpp
    vendor/imgui/backends/imgui_impl_glfw.cpp

    src/main.cpp
    )

add_executable(${PROJ_NAME} ${SOURCES})

target_link_libraries(${PROJ_NAME} PRIVATE glfw)

target_include_directories(${PROJ_NAME} PRIVATE
    ${PROJECT_BINARY_DIR}
    )
