project(groff-grn)

add_darling_executable(grn
	hdb.cpp
	hgraph.cpp
	hpoint.cpp
	main.cpp
)
target_link_libraries(grn
	libgroff
	cxx
)
install(TARGETS grn DESTINATION libexec/darling/usr/bin)
