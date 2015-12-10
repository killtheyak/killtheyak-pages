title: convert files with pandoc
updated: 2015-10-10 11:11:57
description: Some sample file conversions you can do with pandoc.
os: [macosx, linux]
tags: [pandoc]
deps: []
contributors: ["http://www.github.com/anschwa"] 

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
[Official Pandoc demos](http://johnmacfarlane.net/pandoc/demos.html)
