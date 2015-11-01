title: print with a2ps
updated: 2015-10-10 11:10:37
description: Printing from the command line.
os: [macosx, linux]
tags: [a2ps]
deps: []
contributors: ["http://www.github.com/daschwa"] 

How to print on the command line with `a2ps`.

# Print Normally Two-Sided
```
a2ps -1 --portrait --sides=2 -P <printer> <path/to/file>

# Convert to PDF
```
a2ps --delegate no -P pdf </path/to/file>
```

# Connected Printer Status
```
lpstat -p
```

# Connected Printer Location
```
lpstat -c
```
