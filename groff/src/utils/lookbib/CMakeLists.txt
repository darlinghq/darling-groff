project(groff-lookbib)

set(lookbib_sources
	src/src/utils/lookbib/
	${CMAKE_SOURCE_DIR}/src/libstdcxx/src/dso_handle.c
)

add_darling_executable(lookbib
	lookbib.cpp
)
target_link_libraries(lookbib
	libgroff
	groff_bib
	cxx
)
install(TARGETS lookbib DESTINATION libexec/darling/usr/bin)
