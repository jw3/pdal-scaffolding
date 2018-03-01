cmake_minimum_required(VERSION 3.0)
project(pdal-scaffolding)

option(WITH_MATLAB "Add MATLAB integrations" OFF)

if (NOT TARGET_DIR)
    set(TARGET_DIR ${CMAKE_BINARY_DIR}/target)
    message(WARNING "defaulted TARGET_DIR to ${TARGET_DIR}")
endif ()

if (NOT PLUGIN_TYPE)
    set(PLUGIN_TYPE filter)
    message(WARNING "defaulted PLUGIN_TYPE to ${PLUGIN_TYPE}")
endif ()

if (NOT PLUGIN_NAME)
    set(PLUGIN_NAME MyPluginHackName)
    message(WARNING "defaulted PLUGIN_NAME to ${PLUGIN_NAME}")
endif ()

file(COPY common/gitignore DESTINATION ${TARGET_DIR})
file(RENAME ${TARGET_DIR}/gitignore ${TARGET_DIR}/.gitignore)

if (WITH_MATLAB)
    set(INCLUDE_MATLAB "include(matlab)")
    file(COPY common/cmake/matlab.cmake DESTINATION ${TARGET_DIR}/cmake)
endif ()

add_subdirectory(common)
add_subdirectory(filter)
