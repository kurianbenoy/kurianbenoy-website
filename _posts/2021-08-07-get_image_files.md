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

`mimetypes.types_map.items()` returns a dictionary items. It consists of key, value pair and we 
are selecting value pairs starting with the word `image/` to return a set of image_extensions.


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

Let's understand what the function `get_files(path, extensions=None, recurse=True, folders=None, followlinks=True)` is doing line by line.
Let's look at first few lines of code.

```
from fastcore.all import L, setify
from pathlib import Path

def get_files(path, extensions=None, recurse=True, folders=None, followlinks=True):
    "Get all the files in `path` with optional `extensions`, optionally with `recurse`, only in `folders`, if specified."
    path = Path(path)
    folders=L(folders)
    extensions = setify(extensions)
    extensions = {e.lower() for e in extensions}
```

We are converting the path provided to us into a Pathlib object, and folders is converted
to special Python like list called (L) based on `fastcore` library. The extensions are converted to a 
set, if it's being passed as list. All the extensions are converted to lower case characters, if any
extension is in uppper case.

If function definition, we have by default passed `recurse=True`. If it's True, it goes through all the 
files in File path we have passed as well as going inside various folders inside the File Path 
recursively. Else if `recurse=False`, we just goes through all files in the File Path we have passed
without going inside various folder.

```
from fastcore.all import L, setify
from pathlib import Path

def get_files(path, extensions=None, recurse=True, folders=None, followlinks=True):
    ...
    ...
    if recurse:
        ...
        ...
    else:
        f = [o.name for o in os.scandir(path) if o.is_file()]
        res = _get_files(path, f, extensions)
```

For the sake of understanding, let's take an example a `.git` directory, with the following
file structure.

![image](https://user-images.githubusercontent.com/24592806/128638214-f172e126-dfdc-4711-a9ad-7ece27430c04.png)

`os.scandir` returns an iterator of Directory objects. In Python `os` module, there is a `os.listdir(path='.')` which does the exact same functionality as `scandir` which gives a
better performance for many common use cases. [1]

> f = [o.name for o in os.scandir(path) if o.is_file()]

It returns a list of file extensions as shown below with list compreheneshions, where `is_file()` returns, if it's actually file or whether it's pointing to a directory with followlinks.

```
>>> [o.name for o in os.scandir(t) if o.is_file()]
['index', 'HEAD', 'packed-refs', 'config', 'description']
```

If `recurse=True`, it goes through all the directories and work on files
recursively. Let's look at the sources code and try to understand more

 After that it's passed to `_get_files` function, which return the list of filenames to a list
 of pathlib Path of various filenames. 

{% highlight python %}
def _get_files(p, fs, extensions=None):
    p = Path(p)
    res = [p/f for f in fs if not f.startswith('.')
           and ((not extensions) or f'.{f.split(".")[-1].lower()}' in extensions)]
    return res
{% endhighlight %}

`fs`, the list of files returned. We are not passing files which are starting with `.` like `.gitignore or env` as it's not usually very useful for our dataset to get as files. Also it's not returning
file extensions passed or `f'.{f.split(".")[-1].lower()}'` in extensions.

res on passing `p/f` for the list of files will become a list of paths.

```
>> get_files(Path('.'))
[Path('index'), Path('HEAD'), Path('packed-refs'), Path('config'), Path('description'), Path('hooks/fsmonitor-watchman.sample'), Path('hooks/update.sample'), Path('hooks/pre-applypatch.sample'), Path('hooks/pre-push.sample'), Path('hooks/pre-receive.sample'), Path('hooks/applypatch-msg.sample'), Path('hooks/pre-commit.sample'), Path('hooks/prepare-commit-msg.sample'), Path('hooks/commit-msg.sample'), Path('hooks/post-update.sample'), Path('hooks/pre-rebase.sample'), Path('objects/pack/pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.pack'), Path('objects/pack/pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.idx'), Path('info/exclude'), Path('refs/remotes/origin/HEAD'), Path('refs/heads/master'), Path('logs/HEAD'), Path('logs/refs/remotes/origin/HEAD'), Path('logs/refs/heads/master')]
```

This is how the `get_image_files`, returns a L object based on fastcore for any object.
For the BIWI Dataset, the output of `get_image_files` and `get_files` is as following:

![image](https://user-images.githubusercontent.com/24592806/128119162-41abebab-dda4-4d8b-b781-2d81d501b8aa.png)

### Conclusion

I hope with this blogpost, you now have understood how `get_image_files`, fetches
the list of images under the hood by looking into the source code. 

In case, if I have missed something or to provide feedback, please feel free to
reach out to me [@kurianbenoy](https://twitter.com/kurianbenoy2).

### References

[1] https://docs.python.org/3/library/os.html#os.listdir

