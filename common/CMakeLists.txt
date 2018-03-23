configure_file(README.md.in ${TARGET_DIR}/README.md)

if (NOT CONANFILE)
    set(CONANFILE conanfile.py.in)
endif ()
configure_file(${CONANFILE} ${TARGET_DIR}/conanfile.py)

file(COPY cmake/cpack.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/version.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/BuildInfo.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/dependencies.cmake DESTINATION ${TARGET_DIR}/cmake)
