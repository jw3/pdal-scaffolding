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
configure_file(src/T.hpp.in ${TARGET_DIR}/src/${PLUGIN_NAME}.hpp)
configure_file(src/T.cpp.in ${TARGET_DIR}/src/${PLUGIN_NAME}.cpp)


# test
configure_file(test/CMakeLists.txt.in ${TARGET_DIR}/test/CMakeLists.txt @ONLY)
configure_file(test/driver.cpp.in ${TARGET_DIR}/test/driver.cpp)
configure_file(test/UnitTest.cpp.in ${TARGET_DIR}/test/${PLUGIN_NAME}UnitTest.cpp)

if (WITH_MATLAB)
    file(APPEND ${TARGET_DIR}/src/CMakeLists.txt "
set_matlab_rpath(\${PLUGIN_IMPL})
target_link_libraries(\${PLUGIN_IMPL} PRIVATE \${Matlab_MCR_LIBRARIES})
target_include_directories(\${PLUGIN_IMPL} PRIVATE \${Matlab_INCLUDE_DIRS})
")

    file(APPEND ${TARGET_DIR}/test/CMakeLists.txt "
target_link_libraries(\${PLUGIN_TESTS} PRIVATE \${Matlab_MCR_LIBRARIES})
target_include_directories(\${PLUGIN_TESTS} PRIVATE \${Matlab_INCLUDE_DIRS})
")
endif ()
