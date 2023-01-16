---
aliases:
- /2021/08/07/get_image_files
categories:
- TIL
- Python
- fastai
- fastbook
date: '2021-08-07'
gh-repo: fastai/fastai
layout: post
published: true
readtime: true
share-description: get_image_files is used in fastai library to get all image files
  corresponding to a folder path. Let's look how it's actually fetchinging all image_files
  by looking into source, and understanding what it's actually doing.
share-img: /img/fastai.png
show-avatar: false
title: Understanding get_image_files in fastai

---

![](/posts/images/fastai.png)

In **fastai library** we use Datablocks like the below example for loading datasets, and to train models.
The below code is DataBlock, which is used to load a dataset of various types of bears to split
into train and validation datasets along and to resize images to size 128*128. For a detailed explanation, check on From Data to DataLoaders section in [Chapter 2 of Fastbook](From Data to DataLoaders).

```
bears = DataBlock(
    blocks=(ImageBlock, CategoryBlock), 
    get_items=get_image_files, 
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    get_y=parent_label,
    item_tfms=Resize(128))
```

In this Datablock `get_items`, we are using the `get_image_files` to load the images.
I was curious how to see how `get_image_files` worked under the hood to return all the
image files in a dataset. As [Jeremy](https://twitter.com/jeremyphoward) always suggests,
I started looking into source code by handy question mark functionality in Jupyter Notebooks.
 The source code for `get_image_files` can be found in [fastai repo here](https://github.com/fastai/fastai/blob/master/fastai/data/transforms.py). The source code for `get_image_files` function is:

{% highlight python linenos %}
def get_image_files(path, recurse=True, folders=None):
    "Get image files in `path` recursively, only in `folders`, if specified."
    return get_files(path, extensions=image_extensions, recurse=recurse, folders=folders)
{% endhighlight %}

You can see it's expecting the path to the folder where files are present in the image folder.
Also the function signature, consists of `recurse=True` and `folder=None` by default.

You can see `get_image_files` function is calling `get_files(path, extensions=image_extensions, recurse=recurse, folders=folders)` on passing with
extensions set as `image_extensions`. 

> What is image_extensions doing?

{% highlight python linenos %}
import mimetypes

image_extensions = set(k for k,v in mimetypes.types_map.items() if v.startswith('image/'))
{% endhighlight %}

The `image extensions` is just a variable returning a set
of images from the [mimetypes](https://docs.python.org/3/library/mimetypes.html),
which is part of Python standard library to map filenames to MIME types. Let's see `image_extensions` output to
see whole set of image type extensions.

```
>>> image_extensions
{'.jpg', '.svg', '.pgm', '.png', '.xbm', '.jpe', '.pbm', '.pnm', '.rgb', '.tiff', '.xpm', '.jpeg', '.ras', '.ico', '.tif', '.ppm', '.xwd', '.gif', '.bmp', '.ief'}
```

`mimetypes.types_map.items()` returns a dictionary items. It consists of key, value pair and we 
are selecting value pairs starting with the word `image/` to return a set of image_extensions
as shown in the above output.


Now let's look at `get_files` function, which returns a list of files, based on extensions passed, folders. Let's look into the source code of `get_files(path, extensions=None, recurse=True, folders=None, followlinks=True`
 function as well:

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

Let's understand what the function `get_files(path, extensions=None, recurse=True, folders=None, followlinks=True)` is doing line by line.Let's look at the first few lines of code.

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

We are converting the path provided to us into a Pathlib object, and folders are converted
to a special Python-like list called (L) based on the `fastcore` library. The extensions are converted to a 
set if it's being passed as a list, range, string etc. using `setify`. All the extensions are converted to lower case characters if any extension is in upper case. To read more about the `setify` function check
[the fastcore docs](https://fastcore.fast.ai/basics.html#setify).

If function definition, we have by default passed `recurse=True`. If it's True, it goes through all the files in the File path we have passed as well as going inside various folders inside the File Path recursively. Else if `recurse=False`, we just go through all files in the File Path we have passed
without going inside various folders.

```
import os

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

`os.scandir` returns an iterator of Directory objects. In Python `os` module, there is an `os.listdir(path='.')` which does the same functionality as
`scandir`. Yet `scandir` gives a better performance for most of common use cases. [1]

```
f = [o.name for o in os.scandir(path) if o.is_file()]
```

It returns a list of file extensions as shown below with list comprehensions, where `is_file()` returns, if it's a file or whether it's pointing to a directory with `followlinks`.

```
>>> path=Path('.git')
>>> [o.name for o in os.scandir(path) if o.is_file()]
['index', 'HEAD', 'packed-refs', 'config', 'description']
```

If `recurse=True`, it goes through all the directories and works on files
recursively. Let's look at the sources code and try to understand more.

{% highlight python linenos %}
import os

def get_files(path, extensions=None, recurse=True, folders=None, followlinks=True):
    ...
    ...
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
{% endhighlight %}

I would highly recommend the functionality of `os.walk`  by checking this [article](https://www.pythonforbeginners.com/code-snippets-source-code/python-os-walk).
You can see that on iterating through `os.walk()`, we can get the directory path,
and associate file path as a list. This is being passed to `_get_files(p, f, extension)` function.

```
>>> for i,(p,d,f) in enumerate(os.walk(path, followlinks=True)): # returns (dirpath, dirnames, filenames):
...     print(p, f)
...
. ['index', 'HEAD', 'packed-refs', 'config', 'description', '.env']
./.gitignore []
./branches []
./hooks ['fsmonitor-watchman.sample', 'update.sample', 'pre-applypatch.sample', 'pre-push.sample', 'pre-receive.sample', 'applypatch-msg.sample', 'pre-commit.sample', 'prepare-commit-msg.sample', 'commit-msg.sample', 'post-update.sample', 'pre-rebase.sample']
./objects []
./objects/pack ['pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.pack', 'pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.idx']
./objects/info []
./info ['exclude']
./refs []
./refs/tags []
./refs/remotes []
./refs/remotes/origin ['HEAD']
./refs/heads ['master']
./logs ['HEAD']
./logs/refs []
./logs/refs/remotes []
./logs/refs/remotes/origin ['HEAD']
./logs/refs/heads ['master']
```

Just to summarise how the `get_files` function is working it will be useful to look at the below illustration:

![WhatsApp Image 2021-08-09 at 8 12 10 AM](https://user-images.githubusercontent.com/24592806/128655593-d9027327-fd2f-46f4-aebb-140fa9b14e02.jpeg)

When `recurse=False`, for path bears. It returns just returns file README excluding (.gitignore) and directories.

```
>>> get_files(path, recurse=False)
['README']
```

While `recurse=True`, for path bears. It returns all valid files inside the root directory as well as 
in folders such grizzly, black, teddy, details, folder etc.


 After that, it's passed to `_get_files` function, which returns the list of filenames to a list
 of pathlib Path of various filenames. 

{% highlight python linenos %}
def _get_files(p, fs, extensions=None):
    p = Path(p)
    res = [p/f for f in fs if not f.startswith('.')
           and ((not extensions) or f'.{f.split(".")[-1].lower()}' in extensions)]
    return res
{% endhighlight %}

`fs`, the list of files returned. We are not passing files that are starting with `.` like `.gitignore or .env` as it's not usually very useful for our dataset to get as files. Also, it's not returning
file extensions passed or `f'.{f.split(".")[-1].lower()}'` in extensions.

res on passing `p/f` for the list of files will become a list of paths as shown in the below result.
Transforming from a list of file names, we are transforming it to a list of Pathlib module Path,
pointing to various filenames.

```
>> get_files(Path('.'))
[Path('index'), Path('HEAD'), Path('packed-refs'), Path('config'), Path('description'), Path('hooks/fsmonitor-watchman.sample'), Path('hooks/update.sample'), Path('hooks/pre-applypatch.sample'), Path('hooks/pre-push.sample'), Path('hooks/pre-receive.sample'), Path('hooks/applypatch-msg.sample'), Path('hooks/pre-commit.sample'), Path('hooks/prepare-commit-msg.sample'), Path('hooks/commit-msg.sample'), Path('hooks/post-update.sample'), Path('hooks/pre-rebase.sample'), Path('objects/pack/pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.pack'), Path('objects/pack/pack-0ae71ead7e875289ae1c9a4b14ca65dbb7a9fc83.idx'), Path('info/exclude'), Path('refs/remotes/origin/HEAD'), Path('refs/heads/master'), Path('logs/HEAD'), Path('logs/refs/remotes/origin/HEAD'), Path('logs/refs/heads/master')]
```

This is how the `get_image_files`, returns a L object based on fastcore for any object.
For the [BIWI Dataset](https://www.kaggle.com/kmader/biwi-kinect-head-pose-database), the output of `get_image_files` and `get_files` is as following:

![image](https://user-images.githubusercontent.com/24592806/128119162-41abebab-dda4-4d8b-b781-2d81d501b8aa.png)

### Conclusion

I hope with this blog post, you now have understood how `get_image_files`, fetch
the list of images under the hood by looking into the source code. 

In case, if I have missed something or to provide feedback, please feel free to
reach out to me [@kurianbenoy2](https://twitter.com/kurianbenoy2).

### References

[1] [Fastai source code](https://github.com/fastai/fastai)

[2] [Python os module](https://docs.python.org/3/library/os.html#os.listdir)

[3] [Deep Learning for Coders with Fastai and Pytorch: AI Applications Without a PhD
](https://github.com/fastai/fastbook)

