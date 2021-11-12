cmake_minimum_required(VERSION 3.0.0)
project(gtk4test VERSION 0.1.0)

set(GTK_PATH "/home/maxi/usr")
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

message(${GTK_INCLUDE})

add_executable(a main.cpp)

include_directories(
    "${GTK_INCLUDE}" "${GLIB_INCLUDE}"
    "${GLIB_CONFIG_INCLUDE}" "${CAIRO_INCLUDE}"
    "${PANGO_INCLUDE}" "${HARFBUZZ_INCLUDE}"
    "${PIXBUF_INCLUDE}" "${GRAPHENE_INCLUDE}"
    "${GRAPHENE_CONFIG_INCLUDE}"
)

#target_link_libraries(a )

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
