project(groff-tbl)

add_darling_executable(tbl
	main.cpp
	table.cpp
)
target_link_libraries(tbl
	libgroff
	cxx
)
install(TARGETS tbl DESTINATION libexec/darling/usr/bin)
