title: source code to PDF
updated: 2015-10-10 11:10:47
description: This is the template page.
os: [macosx, linux]
tags: [pdf, pandoc, a2ps, pdftk]
deps: []
contributors: ["http://www.github.com/daschwa"] 

Turn source code into a PDF.

1. Use `Org-Mode`
2. Use `Pandoc`
3. Use `a2ps` and `ps2pdf`

# Org-Mode

```
C-x C-e l p
```

# Pandoc
```
pandoc -s example.py -o example.pdf
```

# as2ps

## Convert all .cpp files in a directory

```
for i in ls *.cpp; do a2ps -o $i.ps $i; done;
```

## Convert all .ps files to pdf
```
for i in ls *.ps; do ps2pdf $i; done;
```

(May need to remove empty side-effect `ls.pdf` file).

## Concatenate all output pdf files
```
pdftk *.pdf cat output merged.pdf
```