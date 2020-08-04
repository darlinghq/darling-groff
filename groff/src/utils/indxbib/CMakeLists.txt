project(groff-indxbib)

add_darling_executable(indxbib
	indxbib.cpp
	signal.c
)
target_link_libraries(indxbib
	libgroff
	groff_bib
	cxx
)
install(TARGETS indxbib DESTINATION libexec/darling/usr/bin)
