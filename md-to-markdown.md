title: change all .md to .markdown
updated: 2015-11-01 10:26:04
description: Rename file extensions for all files in a given directory.
os: [macosx, linux]
tags: [bash]
deps: []
contributors: ["http://www.github.com/anschwa"] 

>We no longer live in a 8.3 world, so we should be using the most descriptive file extensions. It’s sad that all our operating systems rely on this stupid convention instead of the better creator code or a metadata model, but great that they now support longer file extensions.

<cite>- Hilton Lipschitz</cite>

[The Markdown File Extension](http://daringfireball.net/linked/2014/01/08/markdown-extension)

```bash
for file in *.md; do mv "$file" "${file%.md}.markdown"; done
```

[source](http://stackoverflow.com/a/1225236)
