project(groff-groff)

add_darling_executable(groff
	groff.cpp

	pipeline.c
)
target_link_libraries(groff
	libgroff
	cxx
)
install(TARGETS groff DESTINATION libexec/darling/usr/bin)
