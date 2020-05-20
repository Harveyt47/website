---
title: Contributing to QuantEcon Lectures
permalink: /contribute-lectures/
menu_item: false
---
# Contributing to QuantEcon Lectures

The QuantEcon Lectures has three different lecture series each have their own repository
* [Python Programming for Economics and Finance](https://github.com/QuantEcon/lecture-python-programming)
* [Quantitative Economics with Python](https://github.com/QuantEcon/lecture-python)
* [Advanced Quantitative Economics with Python](https://github.com/QuantEcon/lecture-python-advanced)

## Building notebooks

All lecture source files are written in reStructuredText. To build a jupyter notebook from these files we use [Jupinx](https://jupinx.quantecon.org).
A jupinx tutorial is available [here](https://jupinx.quantecon.org/tutorial).

## Style Guide - Writing Conventions

If you wish to contribute to these any lecture series, there are a few guidelines to help you along the way.
These are here to maintain consistency across the lectures.

### Mathematical Notation

Matrices always use square brackets. Use `\begin{bmatrix} ... \end{bmatrix}`

Sequences use curly brackets, such as `\{ x_t \}_{t=0}^{\infty}`

The use of align environments can be done using the `\begin{algined} ... \end{aligned}` as it is not a full math environment and works within the equation wrapping of sphinx.

"Independent and identically distributed" is abbreviated to "IID".

The headings should not use math-environment.

Labels must be written in all small alphabetical letters. Any special character should be avoided in labels except "dash" i.e "-"

All the cite key must use the default google scholar bibtex conventions.

Math lines contained in `.. math::` directives should never start with `+` or `-` as they get interpreted as markdown. This is a temporary issue with `nbconvert`

### Emphasis and Definitions

Use **bold** for definitions and _italic_ for emphasis. For example,

* A **closed set** is a set whose complement is open.
* All consumers have _identical_ endowments.

### Titles and Headings

* Capitalization of all words for all titles.
  > Example “How it Works: Data, Variables and Names”

### Adding References

#### Adding a Citation to a Lecture

To add a reference to the text of a QuantEcon lecture you need to use the `:cite:<bibtex-label>` directive.

For example

```
:cite:`StokeyLucas1989`, chapter 2
```

is rendered rendered in HTML and LaTex as:

> [SLP89], chapter 2

#### Adding a new reference to QuantEcon

To add a new reference to the project, a bibtex entry needs to be added to `lecture-source-py/source/_static/quant-econ.bib`.

### Sphinx and Restructured Text

#### Editing

The syntax of the source files is reStructuredText.

[Here is a nice primer](http://sphinx-doc.org/rest.html) on how to write reStructuredText files.

[Here is the documentation](http://jinja.pocoo.org/docs/dev/) for the Jinja template syntax.

### Helpful Links

* [A nice Sphinx tutorial](http://sphinx-doc.org/tutorial.html)
* [Another rst primer](http://docutils.sourceforge.net/docs/user/rst/quickstart.html)

## Building Lectures on OS X

You will need to fetch the Liberation Mono fonts for this repository to build the LaTeX components. 

```bash
brew tap homebrew/cask-fonts
brew cask install font-liberation-sans
brew cask install font-computer-modern
```

## Converting notebooks to RST files

Sometimes it's convenient to write a lecture as a notebook and then convert to
RST

This guide is provided by TJS and requires pandoc 2.6 or newer

(Use `pandoc --version` to test)

1.  This step is necessary only if you want to strip out dollar signs from maths

    *  `python latex_space_strip.py  [myinputfile.ipynb] -o [myoutputfile.ipynb]`

2.  To convert, use

    *  `pandoc [myfilenamenew.pynb] -f ipynb+tex_math_dollars -t rst -s -o [newfilename.rst]`