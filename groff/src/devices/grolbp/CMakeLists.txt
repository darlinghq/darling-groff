project(groff-grolbp)

add_darling_executable(grolbp
	lbp.cpp
)
target_link_libraries(grolbp
	libgroff
	groff_driver
	cxx
)
install(TARGETS grolbp DESTINATION libexec/darling/usr/bin)
