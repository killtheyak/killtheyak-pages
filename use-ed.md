title: use ed
updated: 2015-10-10 11:11:24
description: This is the template page.
os: [macosx, linux]
tags: [ed]
deps: []
contributors: ["http://www.github.com/daschwa"] 

How to use `ed`, a line oriented text editor.

```
ed sample.txt
sample.txt: No such file or directory
```

The message above warns that the sample.txt file is newly created.

```
a
the quick brown fox
jumped over the lazy dog
.
```

That was an append command, which added text to the file.  
The dot on a line by itself terminated the append.

```
1s/f[a-z]x/dragon/
```

On line 1, replace the first substring matching an f followed by a
lowercase alphabetic followed by x with ‘dragon’.  The
substitute command accepts basic regular expressions.

```
1,$p
```

the quick brown dragon
jumped over the lazy dog

Print all lines from 1 to the last.

```
w

51
```

That wrote the file to disk. The ‘q’ command ends the
editing session.

```
q
```

# Reference
[A Tale of Five Editors](http://catb.org/~esr/writings/taoup/html/ch13s02.html)