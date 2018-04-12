configure_file(README.md.in ${TARGET_DIR}/README.md)

if (NOT CONANFILE)
    set(CONANFILE conanfile.py.in)
endif ()
configure_file(${CONANFILE} ${TARGET_DIR}/conanfile.py)

file(COPY cmake/cpack.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/version.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/BuildInfo.cmake DESTINATION ${TARGET_DIR}/cmake)
file(COPY cmake/dependencies.cmake DESTINATION ${TARGET_DIR}/cmake)

if (NOT ${CXX_STANDARD} STREQUAL "17")
    set(BUILD_INFO_STRING_DECL "const std::string")
else ()
    set(BUILD_INFO_STRING_DECL "const std::string")
endif ()
configure_file(BuildInfo.hpp.in ${TARGET_DIR}/src/BuildInfo.hpp.in @ONLY)
