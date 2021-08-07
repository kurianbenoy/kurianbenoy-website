---
title: Understanding get_image_files in fastai codebase
type: post
published: true
tags: [TIL, Python, fastai]
---

In fastai, in chapter 2 for loading the Bear dataset, after downloading. We used the following `DataBlock` to load the dataset:

```
bears = DataBlock(
    blocks=(ImageBlock, CategoryBlock), 
    get_items=get_image_files, 
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    get_y=parent_label,
    item_tfms=Resize(128))
```

In the get_items, we are using the `get_image_files` to load the images. I was curious how to see how get_image_files worked under
the hood to return the image files in a particular directory. The source for [get_image_files can be found in fastai repo](https://github.com/fastai/fastai/blob/master/fastai/data/transforms.py).

If you look at the get_image_files function:

{% highlight python %}
def get_image_files(path, recurse=True, folders=None):
    "Get image files in `path` recursively, only in `folders`, if specified."
    return get_files(path, extensions=image_extensions, recurse=recurse, folders=folders)
{% endhighlight %}

You can see it's expecting where the files are present in the image folder. Also it's calling another function called `get_files` on passing with
extensions `image_extensions`. The `image extensions` is just a variable returning a set of images from the [mimetypes](https://docs.python.org/3/library/mimetypes.html),
which is part of python standard library to map filenames to MIME types. You can checkout the output to see it returns a whole list of image type extensions.

```
import mimetypes

image_extensions = set(k for k,v in mimetypes.types_map.items() if v.startswith('image/'))
```

![image](https://user-images.githubusercontent.com/24592806/128119066-1a898e9f-1fd8-4e90-9cb4-25b5591af430.png)

[File 1]


Now let's look at `get_files` function, which returns a list of files, based on extensions passed in folder path. Let's look into that function
as well:

{% highlight python linenos %}
def get_files(path, extensions=None, recurse=True, folders=None, followlinks=True):
    "Get all the files in `path` with optional `extensions`, optionally with `recurse`, only in `folders`, if specified."
    path = Path(path)
    folders=L(folders)
    extensions = setify(extensions)
    extensions = {e.lower() for e in extensions}
    if recurse:
        res = []
        for i,(p,d,f) in enumerate(os.walk(path, followlinks=followlinks)): # returns (dirpath, dirnames, filenames)
            if len(folders) !=0 and i==0: d[:] = [o for o in d if o in folders]
            else:                         d[:] = [o for o in d if not o.startswith('.')]
            if len(folders) !=0 and i==0 and '.' not in folders: continue
            res += _get_files(p, f, extensions)
    else:
        f = [o.name for o in os.scandir(path) if o.is_file()]
        res = _get_files(path, f, extensions)
    return L(res)
{% endhighlight %}

The extensions are converted to a set, if it's being passed as list. If recurse=True, it goes through all the directories and work on files
recursively. After that it's passed to `_get_files` function, which return the list of files in all those folders. It's finally
returned as a list of foundation object L.

{% highlight python %}
def _get_files(p, fs, extensions=None):
    p = Path(p)
    res = [p/f for f in fs if not f.startswith('.')
           and ((not extensions) or f'.{f.split(".")[-1].lower()}' in extensions)]
    return res
{% endhighlight %}




