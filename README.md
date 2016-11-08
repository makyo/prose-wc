# prose-wc

[![Build Status](https://travis-ci.org/makyo/prose-wc.svg?branch=master)](https://travis-ci.org/makyo/prose-wc) [![Coverage Status](https://coveralls.io/repos/github/makyo/prose-wc/badge.svg?branch=master)](https://coveralls.io/github/makyo/prose-wc?branch=master)

A prose- and Jekyll-aware wordcount utility.

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
