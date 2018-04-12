set(NAMESPACED_NAME ${PLUGIN_NAME})
if (PLUGIN_NAMESPACE)
    set(NAMESPACED_NAME "${PLUGIN_NAMESPACE}_${PLUGIN_NAME}")
endif ()

configure_file(CMakeLists.txt.in ${TARGET_DIR}/CMakeLists.txt @ONLY)

if (ADDITIONAL_INCLUDES)
    string(REPLACE ";" "\n" ADDITIONAL_INCLUDES "${ADDITIONAL_INCLUDES}")
endif ()

# src
configure_file(src/CMakeLists.txt.in ${TARGET_DIR}/src/CMakeLists.txt @ONLY)
configure_file(src/K.hpp.in ${TARGET_DIR}/src/${PLUGIN_NAME}.hpp)
configure_file(src/K.cpp.in ${TARGET_DIR}/src/${PLUGIN_NAME}.cpp)

if (WITH_MATLAB)
    file(APPEND ${TARGET_DIR}/src/CMakeLists.txt "
set_matlab_rpath(\${PLUGIN_IMPL})
target_link_libraries(\${PLUGIN_IMPL} PRIVATE \${Matlab_MCR_LIBRARIES})
target_include_directories(\${PLUGIN_IMPL} PRIVATE \${Matlab_INCLUDE_DIRS})
")
endif ()
