project(groff-libbib)

add_darling_static_library(groff_bib FAT SOURCES
	common.cpp
	index.cpp
	linear.cpp
	search.cpp

	map.c
)
set_target_properties(groff_bib PROPERTIES
	OUTPUT_NAME "bib"
)
