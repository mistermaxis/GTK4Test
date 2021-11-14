cmake_minimum_required(VERSION 3.0.0)
project(gtk4test VERSION 0.1.0)
set(CMAKE_C_STANDARD 11)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/bin")

find_package(PkgConfig REQUIRED)

pkg_check_modules(GTKMM gtkmm-4.0)

INCLUDE_DIRECTORIES(${GTKMM_INCLUDE_DIRS})
LINK_DIRECTORIES(${GTKMM_LIBRARY_DIRS})

ADD_DEFINITIONS(${GTKMM_CFLAGS_OTHER})

add_executable(main main.cpp)

target_compile_features(main PRIVATE cxx_std_17)

target_link_libraries(main PRIVATE ${GTKMM_LIBRARIES})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
