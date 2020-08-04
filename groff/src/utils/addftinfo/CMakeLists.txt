project(groff-addftinfo)

add_darling_executable(addftinfo
	addftinfo.cpp
	guess.cpp
)
target_link_libraries(addftinfo
	libgroff
	cxx
)
install(TARGETS addftinfo DESTINATION libexec/darling/usr/bin)
