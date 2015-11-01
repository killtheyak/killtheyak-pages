title: convert files with pandoc
updated: 2015-10-10 11:11:57
description: This is the template page.
os: [macosx, linux]
tags: [pandoc]
deps: []
contributors: ["http://www.github.com/daschwa"] 

How to use `pandoc` to make Wiki pages or simply convert from one file to another.

# Regular HTML
```
pandoc -s example.txt -o example.html
```

# MediaWiki
```
pandoc -s -S -t mediawiki --toc example.txt -o example.wiki
```

# Reference
http://johnmacfarlane.net/pandoc/demos.html