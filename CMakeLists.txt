cmake_minimum_required(VERSION 3.0.0)
project(gtk4test VERSION 0.1.0)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/bin")

add_executable(a main.cpp)

add_subdirectory("${CMAKE_SOURCE_DIR}/hello")

include_directories("${CMAKE_SOURCE_DIR}/hello/include")

target_link_libraries(a hello)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
