# 3D Regression Heat Map Analysis of Population Study Data

This is the working repository for the paper `3D Regression Heat Map Analysis of Population Study Data`.

### Important files

- `draft.tex` contains the LaTeX input for the paper.
- `Cover Letter.md` contains the feedback from the reviewers based on the `Reviews.md`. It contains [Marked 2](http://marked2app.com/) specific markdown to generate a table of contents.

### Timeline

- [2015-03-31] Submitted to VAST'15.
- [2015-06-07] Conditionally accepted at VAST'15. Reviews can be found at Reviews.md.
- [2015-06-27] Revised version submitted to VAST'15.
- [2015-07-12] Accepted at VAST'15

### Export of Cover Letter to HTML and PDF

The precisionconference.com site does not allow to upload the cover letter as HTML file. [Marked 2](http://marked2app.com/) currently has a bug due to its webkit implementation, which [creates faulty internal links when exported as PDF](http://support.markedapp.com/discussions/questions/3598-saveexport-to-pdf-and-internal-links). The workaround was to export the markdown via Marked 2 to HTML and use [wkhtmltopdf](http://wkhtmltopdf.org/) to create a PDF file with proper links (`wkhtmltopdf Cover\ Letter.html Cover\ Letter.pdf`).

**This repository is licensed under [Attribution-NonCommercial-NoDerivatives 4.0 International](https://creativecommons.org/licenses/by-nc-nd/4.0/)** (see LICENCE.md)
