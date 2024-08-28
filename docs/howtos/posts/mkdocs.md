---
draft: false 
date: 2024-08-27 
categories:
  - mkdocs
tags:
  - mkdocs
# links:
#   - plugins/search.md
#   - insiders/index.md#how-to-become-a-sponsor
# description: Nullam urna elit, malesuada eget finibus ut, ac tortor.
#readtime: 15
---

# mkdocs

## Build and serve locally

TODO
```
VENV = "win_venv"
# TODO create venv if does not exist
python -m venv $VENV --system-site-packages

# activate venv
. ${VENV}/Scripts/activate

echo "Now in venv, updating pip"
python.exe -m pip install --upgrade pip

echo "Installing dependencies"
pip install -r requirements-doc.txt

echo "Building mkdocs"
mkdocs build

mkdocs serve
```

```
no library called "cairo-2" was found
no library called "cairo" was found
no library called "libcairo-2" was found
cannot load library 'libcairo.so.2': error 0x7e.  Additionally, ctypes.util.find_library() did not manage to locate a library called 'libcairo.so.2'
cannot load library 'libcairo.2.dylib': error 0x7e.  Additionally, ctypes.util.find_library() did not manage to locate a library called 'libcairo.2.dylib'
cannot load library 'libcairo-2.dll': error 0x7e.  Additionally, ctypes.util.find_library() did not manage to locate a library called 'libcairo-2.dll'
```

Turned ou that this is the dependency of [`mkdocs-material`](https://github.com/squidfunk/mkdocs-material).
As advised in [docs](https://squidfunk.github.io/mkdocs-material/plugins/requirements/image-processing/#cairo-graphics-windows), installed [msys2](https://www.msys2.org/) and used it to install the cairo library:

```
pacman -S mingw-w64-ucrt-x86_64-cairo
```

Also, add `D:\_system\msys64\ucrt64` to PATH

## Bootstrap

```
pip install mkdocs-material
```

## Bootstrap this repo

First, inside a github account, create empty public github repo named, say just with python `.gitignore` and `README.md`.

Next, on the local machine:

```bash
git clone https://github.com/gh-ka/whatnot.git
cd whatnot
python -m venv win_venv
python.exe -m pip install --upgrade pip
. win_venv/Scripts/activate
pip install mk-docs-material
```

Pip reports that the following packages are installed:
```
Installing collected packages: paginate, watchdog, urllib3, six, regex, pyyaml, pygments, platformdirs, pathspec, packaging, mkdocs-material-extensions, mergedeep, MarkupSafe, markdown, idna, colorama, charset-normalizer, certifi, babel, requests, pyyaml-env-tag, python-dateutil, pymdown-extensions, mkdocs-get-deps, jinja2, click, ghp-import, mkdocs, mkdocs-material
```

Now we can start working in IDE:

```
code .

# and in vscode terminal
which mkdocs    # should pick up the environment
mkdocs new .    # initialize minimal mkdocs site
mkdocs serve    # build and deploy locally to http://127.0.0.1:8000/
```

Configure and modify using documentation.

```
pip install mkdocs-git-revision-date-localized-plugin
```
