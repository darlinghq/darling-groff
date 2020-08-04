project(groff-grodvi)

add_darling_executable(grodvi
	dvi.cpp
)
target_link_libraries(grodvi
	libgroff
	groff_driver
	cxx
)
install(TARGETS grodvi DESTINATION libexec/darling/usr/bin)
