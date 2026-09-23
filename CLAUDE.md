# CV repo

- Build with `latexmk -pdflua cv.tex`, as CI does. Plain `-pdf` fails on the fontawesome icons and `-xelatex` fails on fontspec's Latin Modern lookup; both still write a broken PDF.
- `cv.pdf` is tracked, so never run `latexmk -C` here: it deletes the committed PDF. Use `latexmk -c` to clean auxiliaries only.
- Check a rebuild with `diff <(pdftotext old.pdf -) <(pdftotext cv.pdf -)` against `git show HEAD:cv.pdf`; the date line always changes.
