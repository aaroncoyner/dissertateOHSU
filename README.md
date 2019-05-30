
<!-- README.md is generated from README.Rmd. Please edit that file -->

**This is a fork of
[`dissertateUSU`](https://github.com/TysonStanley/dissertateUSU). I have
simply modified the LaTeX to match OHSU guidelines. Credit goes to
[Tyson
Barrett](https://twitter.com/healthandstats).**

# `dissertateOHSU` `v0.1.0` <img src="inst/OHSU_torch.jpg" align="right" width="20%" height="20%"/>

The goal of `dissertateOHSU` is to make two aspects of writing a
dissertation at Oregon Health & Science University a better experience:

1.  Formatting of the dissertation is automatically done for you
2.  All analyses are intimately tied to the document making the work
    more reproducible

Ultimately, this allows the student to focus on the writing and the
results without having to worry excessively about updating tables and
figures, adjusting formatting of things like the title page and table of
contents, and other minor (but important) aspects of getting the
document correct.

## Installation

You can install `dissertateOHSU` with:

``` r
remotes::install_github("aaroncoyner/dissertateOHSU")
```

## LaTeX

> Importantly, this package requires the new release of LaTeX from your
> preferred distribution. Older versions will often encounter an error
> regarding “\\counterwithin”. If this error comes up for you, then you
> need to update your LaTeX.

## Getting Started

**Adapted from [Tyson
Barrett](https://tysonbarrett.com/jekyll/update/2018/02/11/r_dissertation/)**

The first, and most important file, is the only file you’ll knit. It is
the main .Rmd file, and will be named whatever you have assigned as the
template name. The header YAML in this file looks like this:

<img src="inst/template.png" align="center" width="70%"/>

Most of it contains pieces that, if you’ve used somewhat more advanced
RMarkdown, you are probably familiar with. These include the title,
author, output, bibliography, and nocite. The documentation for this can
be found at RMarkdown’s website. The other pieces are more rare but
still documented as useful YAML options in RMarkdown. Among these,
documentclass: DissertateOHSU is important. This pulls information from
another file called DissertateOHSU.cls, which ultimately controls much
of the formatting of the outputted PDF file. This file was made
particularly to match the specified formatting for Oregon Health &
Science University (thus the dissertateOHSU name) and thus won’t be a
perfect fit for all the other universities. My guess is that it is a
great starting point for you to match your own situation’s guidelines.

This file has comments throughout to highlight what each section is
doing. It includes the formatting of the title page as well. Using the
Params: section of the YAML, the title page is populated with the
information put there. It does this as, while knitting, a file called
preamble.tex is written through a function that is found early in the
RMarkdown file. This function comes through the dissertateOHSU R package
on GitHub (download with
devtools::install\_github(“aaroncoyner/dissertateOHSU”)). After
installing the package, I recommend using the template to get going
using the approach shown below:

Open up a new RMarkdown file:

<img src="inst/dropdownmenu.png" align="center" width="20%"/><br>

Select the “Dissertate OHSU” template:

<img src="inst/fromtemplate.png" align="center" width="60%"/><br>

This will open up a new folder with a skeleton RMarkdown file:

<img src="inst/template.png" align="center" width="70%"/><br>

This produces a document that matches the OHSU dissertation guidelines:

<img src="inst/output.png" align="center" width="70%"/><br>

<br>

In the folder, there are other RMarkdown files called `Chapter1.Rmd`,
`Chapter2.Rmd`, etc. These are the files where you will do the writing
and analyzing. The main RMarkdown file will bring all these files
together into one document. The only things you need to update in the
main RMarkdown file is the `yaml` information, the abstracts,
acknowledgments, and dedication.

For the references, use the BibTex file named bibliography.bib. I used
Mendeley as my references manager and then exported all of my references
to the .bib file. This allowed me to use the regular RMarkdown citing
while using csl: ref\_format.csl (note that it is CSL and not CLS that
is used for the formatting) to format the references correctly (in my
case AMA style). This file was downloaded from the [vast repository of
csl files](https://github.com/citation-style-language/styles). I looked
for the one that fit what I was looking for, downloaded it, and named it
ref\_format.csl and put it in my dissertation’s directory.

## Notes

  - To put the title on two lines (see the thesis cover page above), use
    `\newline` at the point where you want the title to split to the
    second line.
  - If you don’t need a section (e.g., “Chapter 5”, etc.), remove it
    from the main `.Rmd` file. For example, if you want to remove the
    “Chapter 5”, remove all the lines starting from the `\newpage` in
    that section down to the actual words `FILL THIS IN`. It will then
    not be included in the knitted document.
  - For spell checking, use the built-in spell check in RStudio. It’s
    not perfect, but still works well.

## Work in Progress

The package is still undergoing some development and I would love
feedback on any aspect that doesn’t work as expected.

We also want to thank the
[`rticles`](https://github.com/rstudio/rticles) package for the
functionality for `dissertateOHSU`. Many of the functions herein were
derived directly from `rticles`, just with a custom template and LaTeX
style.
