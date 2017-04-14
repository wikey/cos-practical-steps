We here are using pandoc to build a reveal.js presentation as per the
instructions on:
https://github.com/jgm/pandoc/wiki/Using-pandoc-to-produce-reveal.js-slides

This involves making a custom template and using it in addition to
pandoc's "reactjs" output type.  Simply using pandoc's output type
alone failed to build the presentation for me, most likely because I
am on an older version of pandoc (1.12.4.2) until Debian stable moves
from jessie to stretch.

## Revealjs customization options

Because we are using a custom template we lose access to much of
pandoc's helpful functionality including built-in option handling for
setting revealjs theme and other configuration options, using metadata
from the yaml document header to build a title slide and populate
corresponding html page attributes.  Instead we will make those
changes by editing the template.revealjs file directly.

**Note** that page metadata *is* included in the normal yaml header
block within the presentation.md file.  This is done primarially for
use with non-revealjs slide systems and so that all the content is in
the appropriate place for processing with standard pandoc commands
once revealjs export works out of the box.  If you are using these
files as a base for your own presentation make sure to change the
information in both places, or just to change it in template file and
remove it from the yaml.

## Building

To build the presentation make sure that the markdown source file is
in the same directory as the reactjs files and run the following
pandoc command:

```
pandoc --section-divs -t revealjs -s --template template.revealjs -o presentation.html presentation.md
```
