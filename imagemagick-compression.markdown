title: compress images
updated: 2015-10-10 11:10:19
description: Sometimes images are just too big!
os: [macosx, linux]
tags: [imagemagick]
deps: []
contributors: ["http://www.github.com/daschwa"] 

Use `ImageMagick` to healthily compress JPEG images.

# Compressing JPEG

- quality in 85
- progressive (comprobed compression)
- a very tiny gausssian blur to optimize the size (0.05 or 0.5 of radius) depends on the quality and size of the picture, this notably optimizes the size of the jpeg.
- Strip any comment or exif tag

```
convert -strip -interlace Plane -gaussian-blur 0.05 -quality 85% source.jpg result.jpg
```

# Reference
[citation](http://stackoverflow.com/questions/7261855/recommendation-for-compressing-jpg-files-with-imagemagick).
