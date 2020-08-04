project(groff-eqn)

add_darling_executable(eqn
	box.cpp
	delim.cpp
	eqn.cpp
	lex.cpp
	limit.cpp
	list.cpp
	main.cpp
	mark.cpp
	other.cpp
	over.cpp
	pile.cpp
	script.cpp
	special.cpp
	sqrt.cpp
	text.cpp
)
target_link_libraries(eqn
	libgroff
	cxx
)
install(TARGETS eqn DESTINATION libexec/darling/usr/bin)
