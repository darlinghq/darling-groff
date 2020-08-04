project(groff-libdriver)

add_darling_static_library(groff_driver FAT SOURCES
	input.cpp
	printer.cpp
)
set_target_properties(groff_driver PROPERTIES
	OUTPUT_NAME "driver"
)
