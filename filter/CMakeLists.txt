set(NAMESPACED_NAME ${PLUGIN_NAME})
if (PLUGIN_NAMESPACE)
    set(NAMESPACED_NAME "${PLUGIN_NAMESPACE}_${PLUGIN_NAME}")
endif ()

configure_file(CMakeLists.txt.in ${TARGET_DIR}/CMakeLists.txt @ONLY)

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
include(matlab)
set_matlab_rpath(\${PLUGIN_IMPL})
")
endif ()
