project(groff-grolj4)

add_darling_executable(grolj4
	lj4.cpp
)
target_link_libraries(grolj4
	libgroff
	groff_driver
	cxx
)
install(TARGETS grolj4 DESTINATION libexec/darling/usr/bin)
