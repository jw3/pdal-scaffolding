configure_file(README.md.in ${TARGET_DIR}/README.md)

if (NOT CONANFILE)
    set(CONANFILE conanfile.py.in)
endif ()
configure_file(${CONANFILE} ${TARGET_DIR}/conanfile.py)
