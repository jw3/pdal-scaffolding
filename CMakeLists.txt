cmake_minimum_required(VERSION 3.0)
project(pdal-scaffolding)

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


add_subdirectory(common)
add_subdirectory(filter)