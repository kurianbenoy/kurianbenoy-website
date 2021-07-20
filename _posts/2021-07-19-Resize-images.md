---
title: Resizing an image to smaller size
type: post
tags: [TIL, Python]
author: 'Kurian Benoy'
---

Resizing images to smaller dimension to satisfy the file size or height/width requirements is something we have faced multiple times.
Most of the online tools which I previously used were full of advertisments, and even required to login which is something I hated a lot.
Today I learned to do this tedious job with python and it's pretty easy also.

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

