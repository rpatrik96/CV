# CV repo

- Build with `latexmk -pdflua cv.tex`, as CI does. Plain `-pdf` fails on the fontawesome icons and `-xelatex` fails on fontspec's Latin Modern lookup; both still write a broken PDF.
- `cv.pdf` is tracked, so never run `latexmk -C` here: it deletes the committed PDF. Use `latexmk -c` to clean auxiliaries only.
- A cover letter goes in front of the CV as one PDF, in the CV's own style: put the letter in `coverletter_<name>.tex` (moderncv letter commands, see `coverletter_gresearch.tex`) and build `latexmk -pdflua -jobname=bundle_<name> -usepretex='\def\coverletter{coverletter_<name>}' cv.tex`. Both files are gitignored; the plain `cv.pdf` build ignores the hook.
- Check a rebuild with `diff <(pdftotext old.pdf -) <(pdftotext cv.pdf -)` against `git show HEAD:cv.pdf`; the date line always changes.
