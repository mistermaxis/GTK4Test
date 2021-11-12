cmake_minimum_required(VERSION 3.0.0)
project(gtk4test VERSION 0.1.0)

set(GTK_PATH "/home/maxi/usr")
set(GTK_LIB_PATH "${GTK_PATH}/lib/x86_64-linux-gnu/")
set(GTK_INCLUDE "${GTK_PATH}/include/gtk-4.0")
set(GLIB_INCLUDE "${GTK_PATH}/include/glib-2.0")
set(GLIB_CONFIG_INCLUDE "${GTK_PATH}/lib/x86_64-linux-gnu/glib-2.0/include")
set(CAIRO_INCLUDE "${GTK_PATH}/include/cairo")
set(PANGO_INCLUDE "${GTK_PATH}/include/pango-1.0")
set(HARFBUZZ_INCLUDE "${GTK_PATH}/include/harfbuzz")
set(PIXBUF_INCLUDE "${GTK_PATH}/include/gdk-pixbuf-2.0")
set(GRAPHENE_INCLUDE "${GTK_PATH}/include/graphene-1.0")
set(GRAPHENE_CONFIG_INCLUDE "${GTK_PATH}/lib/x86_64-linux-gnu/graphene-1.0/include")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/bin")

add_executable(a main.cpp)

include_directories(
    "${GTK_INCLUDE}" "${GLIB_INCLUDE}"
    "${GLIB_CONFIG_INCLUDE}" "${CAIRO_INCLUDE}"
    "${PANGO_INCLUDE}" "${HARFBUZZ_INCLUDE}"
    "${PIXBUF_INCLUDE}" "${GRAPHENE_INCLUDE}"
    "${GRAPHENE_CONFIG_INCLUDE}"
)

target_link_directories(a PUBLIC
    "${GTK_PATH}/lib/"
    "${GTK_LIB_PATH}"
)

find_library(gtklib gtk-4 NAMES gtk libgtk PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)
find_library(golib gobject-2.0 NAMES libgobject PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)
find_library(giolib gio-2.0 NAMES libgio PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)
find_library(pangoft pangoft2-1.0 NAMES pangoft2 PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)
find_library(pangolib pango-1.0 NAMES pango1 PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)
find_library(glib glib-2.0 NAMES glib-2 PATHS "${GTK_LIB_PATH}" NO_DEFAULT_PATH)

message(${glib})

target_link_libraries(a PUBLIC ${gtklib} PUBLIC ${glib} PUBLIC ${golib} PUBLIC ${giolib} PUBLIC ${pangoft} PUBLIC ${pangolib})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
