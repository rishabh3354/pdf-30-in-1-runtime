# pdf-30-in-1-runtime

Content snap with everything the PDF 30-in-1 snap needs on top of core22: desktop libraries, fonts,
themes and locales (the same set as content-snap-core22-lite, minus the fonts it doesn't use), plus
LibreOffice, Tesseract and Ghostscript.

PDF 30-in-1 plugs it at `$SNAP/pdf-30-in-1-runtime` (`default-provider`, so it installs with the app),
and its launcher (`snap_launcher/bin/desktop-launch`, `RUNTIME_NAME`) adds the runtime's libraries and
programs to the app's environment.

See cmd.txt for building and uploading.
