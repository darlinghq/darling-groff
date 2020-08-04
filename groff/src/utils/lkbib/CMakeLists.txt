project(groff-lkbib)

add_darling_executable(lkbib
	lkbib.cpp
)
target_link_libraries(lkbib
	libgroff
	groff_bib
	cxx
)
install(TARGETS lkbib DESTINATION libexec/darling/usr/bin)
