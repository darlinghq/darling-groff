project(groff-soelim)

add_darling_executable(soelim
	soelim.cpp
)
target_link_libraries(soelim
	libgroff
	cxx
)
install(TARGETS soelim DESTINATION libexec/darling/usr/bin)
