cmake_minimum_required(VERSION 3.14)
set(CMAKE_CONFIGURATION_TYPES "Debug;Release")

project(Basic-Fluid)

set(SOURCES
	src/drawloop.cpp
	src/main.cpp
)

set(HEADERS
	include/drawloop.h
)

add_library(glfw STATIC IMPORTED)
set_target_properties(glfw PROPERTIES
	IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/third-party/bin/glfw/lib-vc2017/glfw3.lib
)

add_executable(fluid ${SOURCES} ${HEADERS})

target_include_directories(fluid PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_include_directories(fluid PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/third-party/include)

target_link_libraries(fluid PRIVATE glfw)
target_link_libraries(fluid PRIVATE opengl32)

target_compile_options(fluid PRIVATE "/WX") # Treat warnings as errors
