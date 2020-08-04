project(groff-hpftodit)

add_darling_executable(hpftodit
	hpftodit.cpp
	hpuni.cpp
)
target_link_libraries(hpftodit
	libgroff
	cxx
)
install(TARGETS hpftodit DESTINATION libexec/darling/usr/bin)
