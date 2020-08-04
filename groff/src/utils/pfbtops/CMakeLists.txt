project(groff-pfbtops)

add_darling_executable(pfbtops
	pfbtops.c
)
target_link_libraries(pfbtops
	libgroff
	cxx
)
install(TARGETS pfbtops DESTINATION libexec/darling/usr/bin)
