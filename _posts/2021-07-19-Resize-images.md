---
title: Resizing an image to smaller size
type: post
tags: [TIL, Python]
author: 'Kurian Benoy'
---

Resizing images to smaller dimension to meet size requirements is needed for most of application processes in India like Entrance Exams.
It has been needed recently to resize some images for this website, when writing articles.  always relied some online tools to resize, which is full of ads.
Recently I tried to do it with Python and pretty easy to do it.

Library used: Pillow

```
import os, sys
from PIL import Image

size = (720, 720)

for infile in sys.argv[1:]:
    outfile = os.path.splitext(infile)[0] + f"{size[0]}.jpg"
    if infile != outfile:
        try:
            with Image.open(infile) as im:
                im.thumbnail(size)
                im.save(outfile, "JPEG")
        except OSError:
            print("cannot create thumbnail for", infile)
            
```

Save file as `resize.py` and run the script with:

> python3 resize.py image.jpg

