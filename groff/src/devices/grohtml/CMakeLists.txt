project(groff-grohtml)

add_darling_executable(post-grohtml
	html-table.cpp
	html-text.cpp
	output.cpp
	post-html.cpp
)
target_link_libraries(post-grohtml
	libgroff
	groff_driver
	cxx
)
install(TARGETS post-grohtml DESTINATION libexec/darling/usr/bin)
