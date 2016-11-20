project(groff)

cmake_minimum_required(VERSION 2.4.0)

include(darling_exe)

include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(BEFORE ${CMAKE_CURRENT_SOURCE_DIR}/src/src/include)
include_directories(BEFORE ${CMAKE_CURRENT_SOURCE_DIR}/gen/include)
include_directories(${DARLING_TOP_DIRECTORY}/src/libc/include/FreeBSD)

add_definitions(-DHAVE_CONFIG_H -D__GETOPT_PREFIX=groff_ -D_LIBC)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fwrapv -fPIC -ggdb -Wno-implicit-function-declaration -Wno-int-conversion")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC -Wno-missing-exception-spec -Wno-unused-value")
set(CMAKE_SHARED_LINKER_FLAGS "-nodefaultlibs -nostdlib -fPIC -Wl,--version-script=${DARLING_TOP_DIRECTORY}/darwin.map")
set(CMAKE_EXE_LINKER_FLAGS "-nodefaultlibs -nostdlib -fPIC -Wl,--version-script=${DARLING_TOP_DIRECTORY}/darwin.map")

SET(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR}/darling")
SET(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)
SET(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)


set(libgroff_sources
	src/src/libs/libgroff/assert.cpp
	src/src/libs/libgroff/change_lf.cpp
	src/src/libs/libgroff/cmap.cpp
	src/src/libs/libgroff/color.cpp
	src/src/libs/libgroff/cset.cpp
	src/src/libs/libgroff/device.cpp
	src/src/libs/libgroff/errarg.cpp
	src/src/libs/libgroff/error.cpp
	src/src/libs/libgroff/fatal.cpp
	src/src/libs/libgroff/filename.cpp
	src/src/libs/libgroff/font.cpp
	src/src/libs/libgroff/fontfile.cpp
	src/src/libs/libgroff/geometry.cpp
	src/src/libs/libgroff/getopt.c
	src/src/libs/libgroff/getopt1.c
	src/src/libs/libgroff/glyphuni.cpp
	src/src/libs/libgroff/htmlhint.cpp
	src/src/libs/libgroff/hypot.cpp
	src/src/libs/libgroff/iftoa.c
	src/src/libs/libgroff/itoa.c
	src/src/libs/libgroff/invalid.cpp
	src/src/libs/libgroff/lf.cpp
	src/src/libs/libgroff/lineno.cpp
	src/src/libs/libgroff/macropath.cpp
	src/src/libs/libgroff/matherr.c
	src/src/libs/libgroff/maxfilename.cpp
	src/src/libs/libgroff/maxpathname.cpp
	src/src/libs/libgroff/mksdir.cpp
	src/src/libs/libgroff/nametoindex.cpp
	src/src/libs/libgroff/new.cpp
	src/src/libs/libgroff/paper.cpp
	src/src/libs/libgroff/prime.cpp
	src/src/libs/libgroff/progname.c
	src/src/libs/libgroff/ptable.cpp
	src/src/libs/libgroff/quotearg.c
	src/src/libs/libgroff/relocate.cpp
	src/src/libs/libgroff/searchpath.cpp
	src/src/libs/libgroff/spawnvp.c
	src/src/libs/libgroff/string.cpp
	src/src/libs/libgroff/strsave.cpp
	src/src/libs/libgroff/symbol.cpp
	src/src/libs/libgroff/tmpfile.cpp
	src/src/libs/libgroff/tmpname.cpp
	src/src/libs/libgroff/unicode.cpp
	src/src/libs/libgroff/uniglyph.cpp
	src/src/libs/libgroff/uniuni.cpp
	gen/version-libgroff.cpp
	${DARLING_TOP_DIRECTORY}/src/libstdcxx/src/dso_handle.c
)

add_library(groff STATIC ${libgroff_sources})


set(troff_sources
	src/src/roff/troff/dictionary.cpp
	src/src/roff/troff/div.cpp
	src/src/roff/troff/env.cpp
	src/src/roff/troff/input.cpp
	gen/src/majorminor.cpp
	src/src/roff/troff/mtsm.cpp
	src/src/roff/troff/node.cpp
	src/src/roff/troff/number.cpp
	src/src/roff/troff/reg.cpp
)

add_darling_executable(troff ${troff_sources})
target_link_libraries(troff system groff stdcxx)
install(TARGETS troff DESTINATION libexec/darling/usr/bin)


set(tbl_sources
	src/src/preproc/tbl/table.cpp
	src/src/preproc/tbl/main.cpp
)

add_darling_executable(tbl ${tbl_sources})
target_link_libraries(tbl system groff stdcxx)
install(TARGETS tbl DESTINATION libexec/darling/usr/bin)


set(pic_sources
	src/src/preproc/pic/pic.cpp
	src/src/preproc/pic/lex.cpp
	src/src/preproc/pic/common.cpp
	src/src/preproc/pic/main.cpp
	src/src/preproc/pic/object.cpp
	src/src/preproc/pic/tex.cpp
	src/src/preproc/pic/troff.cpp
)

add_darling_executable(pic ${pic_sources})
target_link_libraries(pic system groff stdcxx)
install(TARGETS pic DESTINATION libexec/darling/usr/bin)


set(eqn_sources
	src/src/preproc/eqn/eqn.cpp
	src/src/preproc/eqn/main.cpp
	src/src/preproc/eqn/lex.cpp
	src/src/preproc/eqn/box.cpp
	src/src/preproc/eqn/limit.cpp
	src/src/preproc/eqn/list.cpp
	src/src/preproc/eqn/over.cpp
	src/src/preproc/eqn/text.cpp
	src/src/preproc/eqn/script.cpp
	src/src/preproc/eqn/mark.cpp
	src/src/preproc/eqn/other.cpp
	src/src/preproc/eqn/delim.cpp
	src/src/preproc/eqn/sqrt.cpp
	src/src/preproc/eqn/pile.cpp
	src/src/preproc/eqn/special.cpp
)

add_darling_executable(eqn ${eqn_sources})
target_link_libraries(eqn system groff stdcxx)
install(TARGETS eqn DESTINATION libexec/darling/usr/bin)


set(grn_sources
	src/src/preproc/grn/hdb.cpp
	src/src/preproc/grn/hpoint.cpp
	src/src/preproc/grn/hgraph.cpp
	src/src/preproc/grn/main.cpp
)

add_darling_executable(grn ${grn_sources})
target_link_libraries(grn system groff stdcxx)
install(TARGETS grn DESTINATION libexec/darling/usr/bin)


set(refer_sources
	src/src/preproc/refer/command.cpp
	src/src/preproc/refer/label.cpp
	src/src/preproc/refer/ref.cpp
	src/src/preproc/refer/refer.cpp
	src/src/preproc/refer/token.cpp
)

add_darling_executable(refer ${refer_sources})
target_link_libraries(refer system groff stdcxx)
install(TARGETS refer DESTINATION libexec/darling/usr/bin)


set(soelim_sources
	src/src/preproc/soelim/soelim.cpp
)

add_darling_executable(soelim ${soelim_sources})
target_link_libraries(soelim system groff stdcxx)
install(TARGETS soelim DESTINATION libexec/darling/usr/bin)


set(pre-grohtml_sources
	src/src/preproc/html/pre-html.cpp
	src/src/preproc/html/pushback.cpp
)

add_darling_executable(pre-grohtml ${pre-grohtml_sources})
target_link_libraries(pre-grohtml system groff stdcxx)
install(TARGETS pre-grohtml DESTINATION libexec/darling/usr/bin)


# Static content
install(DIRECTORY gen/usr DESTINATION libexec/darling)
