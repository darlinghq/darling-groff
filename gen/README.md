# gen folders
Files here were generated during a build for a real Mac, and should be kept seperate from unmodified source directories

Most of the files are just the results of running `configure` and `make`, but the `usr` directory contains some static files (e.g. scripts and data files) installed using `make prefix=$PWD/usr install` (because groff doesn't support DESTDIR for some reason).
