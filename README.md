# pdf-30-in-1-runtime

Content snap with everything the PDF 30-in-1 snap needs on top of core22: desktop libraries, fonts,
themes and locales (the same set as content-snap-core22-lite, minus the fonts it doesn't use), plus
LibreOffice, Tesseract and Ghostscript.

PDF 30-in-1 plugs it at `$SNAP/pdf-30-in-1-runtime` (`default-provider`, so it installs with the app),
and its launcher (`snap_launcher/bin/desktop-launch`, `RUNTIME_NAME`) adds the runtime's libraries and
programs to the app's environment.

See cmd.txt for building and uploading.

Notes:
- snapcraft takes LibreOffice from jammy-backports (26.x, newer than jammy's 7.3) - it works, but check
  `usr/lib/libreoffice/program/versionrc` after a rebuild.
- The runtime's `usr/lib/x86_64-linux-gnu` (first on the launcher's library path) holds copies of
  LibreOffice's UNO libraries, which can't find the rest of LibreOffice from there; PDF 30-in-1 puts
  `usr/lib/libreoffice/program` first when it starts LibreOffice (engine/office.py, soffice_launch).
- Test a conversion inside the app snap before releasing a new runtime:
  `snap run --shell pdf-30-in-1`, then run soffice --headless --convert-to pdf on a .docx.
