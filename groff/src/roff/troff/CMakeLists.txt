project(groff-troff)

add_darling_executable(troff
	dictionary.cpp
	div.cpp
	env.cpp
	input.cpp
	mtsm.cpp
	node.cpp
	number.cpp
	reg.cpp
	
	../../../../gen/src/roff/troff/majorminor.cpp
)
target_link_libraries(troff
	libgroff
	cxx
)
install(TARGETS troff DESTINATION libexec/darling/usr/bin)
