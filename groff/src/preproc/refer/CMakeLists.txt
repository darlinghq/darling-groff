project(groff-refer)

add_darling_executable(refer
	command.cpp
	label.cpp
	ref.cpp
	refer.cpp
	token.cpp
)
target_link_libraries(refer
	libgroff
	groff_bib
	cxx
)
install(TARGETS refer DESTINATION libexec/darling/usr/bin)
