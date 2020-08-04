project(groff-pic)

add_darling_executable(pic
	pic.cpp
	lex.cpp
	main.cpp
	object.cpp
	common.cpp
	troff.cpp
	tex.cpp
)
target_link_libraries(pic
	libgroff
	cxx
)
install(TARGETS pic DESTINATION libexec/darling/usr/bin)
