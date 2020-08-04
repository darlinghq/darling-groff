project(groff-grotty)

add_darling_executable(grotty
	tty.cpp
)
target_link_libraries(grotty
	libgroff
	groff_driver
	cxx
)
install(TARGETS grotty DESTINATION libexec/darling/usr/bin)
