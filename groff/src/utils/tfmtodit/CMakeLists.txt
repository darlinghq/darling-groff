project(groff-tfmtodit)

add_darling_executable(tfmtodit
	tfmtodit.cpp
)
target_link_libraries(tfmtodit
	libgroff
	cxx
)
install(TARGETS tfmtodit DESTINATION libexec/darling/usr/bin)
