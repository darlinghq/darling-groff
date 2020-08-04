project(groff-grops)

add_darling_executable(grops
	ps.cpp
	psrm.cpp
)
target_link_libraries(grops
	libgroff
	groff_driver
	cxx
)
install(TARGETS grops DESTINATION libexec/darling/usr/bin)
