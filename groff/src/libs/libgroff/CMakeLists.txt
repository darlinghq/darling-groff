project(groff-libgroff)

add_darling_static_library(libgroff FAT SOURCES
	assert.cpp
	change_lf.cpp
	cmap.cpp
	color.cpp
	cset.cpp
	device.cpp
	errarg.cpp
	error.cpp
	fatal.cpp
	filename.cpp
	font.cpp
	fontfile.cpp
	geometry.cpp
	glyphuni.cpp
	htmlhint.cpp
	hypot.cpp
	invalid.cpp
	lf.cpp
	lineno.cpp
	macropath.cpp
	maxfilename.cpp
	maxpathname.cpp
	mksdir.cpp
	nametoindex.cpp
	new.cpp
	paper.cpp
	prime.cpp
	ptable.cpp
	relocate.cpp
	searchpath.cpp
	string.cpp
	strsave.cpp
	symbol.cpp
	tmpfile.cpp
	tmpname.cpp
	unicode.cpp
	uniglyph.cpp
	uniuni.cpp

	getopt.c
	getopt1.c
	iftoa.c
	itoa.c
	matherr.c
	progname.c
	quotearg.c
	spawnvp.c

	../../../../gen/src/libs/libgroff/version.cpp
)
set_target_properties(libgroff PROPERTIES
	OUTPUT_NAME "groff"
)
