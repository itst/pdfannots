# About

This is a script that extracts annotations (highlights, comments,
etc.) from a PDF file, and formats them as plain text.

At present, the following annotations are supported:

 * Highlights without an attached comment are output first, as
   "highlights" with just the highlighted text included.

 * Highlights with an attached comment, and text annotations (not
   attached to any particular text/highlight) are output next, as
   "detailed comments".

 * Underline, strikeout, and squiggly underline annotations are output
   last, as "Nits", with or without an attached comment. The intention
   of this is to easily separate formatting or grammatical corrections
   from more substantial comments about the content of the document.

For each annotation, the page number is given, along with the
associated (highlighted/underlined) text, if any. Additionally, if the
documents includes outlines (aka bookmarks) such as those generated by
the hyperref package, those are also used to identify to which section
in the document the annotation refers.

# Usage

    pdf-highlights.py INPUT > OUTPUT

# Limitations

At present the script has a number of limitations:

 * pdfminer (the underlying PDF parser) sometimes fails to extract
   text from PDF files when other converters (e.g. pdftotext) do just
   fine; this results in annotations with missing (or no) text
   associated with them
 * pdfminer isn't the fastest piece of software :)
 * The output from strikeout annotations is not very meaningful

# Dependencies
 
 My own setup:
 * Python 3.6
 * chardet (3.0.4)
 * colormath (3.0.0)
 * Jinja2 (2.10)
 * pathlib (1.0.1)
 * pdfminer.six (20170720)
 * six (1.11.0)

# Installation
 
     pip install pdfminer.six chardet six colormath Jinja2 pathlib
     python setup.py install

# FAQ

## I'd like to change how the output is formatted.

There's a Jinja2 template you can adopt as you like. The script exposes the following data to the template:
 * highlights
 * comments
 * Author
 * Title

# Author

Original author is Andrew Baumann. Thank you, Andrew!
This fork is maintained by Sascha A. Carlin.
