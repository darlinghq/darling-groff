project(groff)

cmake_minimum_required(VERSION 2.4.0)

include_directories(BEFORE
	${CMAKE_CURRENT_SOURCE_DIR}/groff/src/include
	${CMAKE_CURRENT_SOURCE_DIR}/gen/src/include
)

add_compile_definitions(
	HAVE_CONFIG_H
	__GETOPT_PREFIX=groff_
)

add_definitions(
	-Wno-format-security
	-Wno-implicit-function-declaration
	-Wno-int-conversion
	-Wno-missing-exception-spec
	-Wno-unused-value
	-Wno-parentheses
	-Wno-tautological-pointer-compare
	-Wno-mismatched-new-delete
)

# not sure if we really need to add `-fPIC` in individual projects (i.e. i'm also talking about other submodules that have it)
# because the root CMakeLists already sets it conditionally if position-independent code is enabled for CMake
# (which i believe is enabled by default)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fwrapv -fPIC")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC")

add_subdirectory(groff/src/libs/libgroff)
add_subdirectory(groff/src/libs/libdriver)
add_subdirectory(groff/src/libs/libbib)

add_subdirectory(groff/src/roff/groff)
add_subdirectory(groff/src/roff/troff)

add_subdirectory(groff/src/preproc/tbl)
add_subdirectory(groff/src/preproc/pic)
add_subdirectory(groff/src/preproc/eqn)
add_subdirectory(groff/src/preproc/grn)
add_subdirectory(groff/src/preproc/refer)
add_subdirectory(groff/src/preproc/soelim)
add_subdirectory(groff/src/preproc/html)

add_subdirectory(groff/src/devices/grops)
add_subdirectory(groff/src/devices/grotty)
add_subdirectory(groff/src/devices/grodvi)
add_subdirectory(groff/src/devices/grolj4)
add_subdirectory(groff/src/devices/grohtml)
add_subdirectory(groff/src/devices/grolbp)

add_subdirectory(groff/src/utils/tfmtodit)
add_subdirectory(groff/src/utils/hpftodit)
add_subdirectory(groff/src/utils/lookbib)
add_subdirectory(groff/src/utils/indxbib)
add_subdirectory(groff/src/utils/lkbib)
add_subdirectory(groff/src/utils/addftinfo)
add_subdirectory(groff/src/utils/pfbtops)

# Static content
install(DIRECTORY gen/fakeroot/usr DESTINATION libexec/darling USE_SOURCE_PERMISSIONS)

InstallSymlink("grohtml.1" "${CMAKE_INSTALL_PREFIX}/libexec/darling/usr/share/man/man1/pre-grohtml.1")
InstallSymlink("grohtml.1" "${CMAKE_INSTALL_PREFIX}/libexec/darling/usr/share/man/man1/post-grohtml.1")
InstallSymlink("groff_mdoc.7" "${CMAKE_INSTALL_PREFIX}/libexec/darling/usr/share/man/man7/mdoc.7")
