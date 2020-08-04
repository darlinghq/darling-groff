project(groff-html)

add_darling_executable(pre-grohtml
	pre-html.cpp
	pushback.cpp
)
target_link_libraries(pre-grohtml
	libgroff
	cxx
)
install(TARGETS pre-grohtml DESTINATION libexec/darling/usr/bin)
