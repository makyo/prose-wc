# prose-wc

[![Build Status](https://travis-ci.org/makyo/prose-wc.svg?branch=master)](https://travis-ci.org/makyo/prose-wc) [![Coverage Status](https://coveralls.io/repos/github/makyo/prose-wc/badge.svg?branch=master)](https://coveralls.io/github/makyo/prose-wc?branch=master) [![PyPI](https://img.shields.io/pypi/v/prose-wc.svg)](https://pypi.python.org/pypi/prose-wc/)

A prose- and Jekyll-aware wordcount utility.

## Installing 

    pip install prose-wc

## Running

```
usage: prose-wc [-h] [-u] [-f [{yaml,json,default}]] [-i [INDENT]] file

Compute Jekyl- and prose-aware wordcounts

positional arguments:
  file                  file to count (or - for STDIN)

optional arguments:
  -h, --help            show this help message and exit
  -u, --update          update the jekyll file in place with the counts. Does
                        nothing if the file is not a Jekyll markdown file.
                        Implies format=yaml, invalid with input from STDIN and
                        non-Jekyll files.
  -f [{yaml,json,default}], --format [{yaml,json,default}]
                        output format.
  -i [INDENT], --indent [INDENT]
                        indentation depth (default: 4).

Accepted filetypes: plaintext, markdown, markdown (Jekyll)
```

Running `prose-wc` against a file will generate a series of counts that might be of use.  You can get these counts in a simple, tab-separated format, JSON, or YAML.  If you're working with a Jekyll markdown file, you can also choose to have this data embedded in the frontmatter as YAML.

## Other filetypes

You can use [pandoc](http://pandoc.org) to convert your file and pipe it into prose-wc:

    pandoc -f latex -t plain my_great_story.tex | prose-wc -
    
## In a Jekyll site

You can add wordcount information to your site in some place handy such as at the top of a post in `_layouts/post.html` with:

```liquid
{% if page.counts %}
    <p class="text-muted small">
        {{ page.counts.paragraphs }} {% if page.counts.paragraphs == 1 %}paragraph{% else %}paragraphs{% endif %} &bullet;
        {{ page.counts.words }} words
    </p>
{% endif %}
```

This would result in something like [this](http://writing.drab-makyo.com/posts/tasting/2016/09/17/teas-of-late/).
     
You can add wordcounts to posts with a find command like:

    find . \( -name '*.md' -or -name '*.markdown' \) -exec prose-wc -u "{}" \;
