This is a collection of unsorted writings - notes, howtos, thoughts, etc., accumilated over time.

The contents are hosted on [github](https://github.com/gh-ka/whatnot), powered by [mkdocs-material](squidfunk.github.io/mkdocs-material/), and published on [GithubPages](https://gh-ka.github.io/whatnot) using custom [github action](.github/workflows/mkdocs.yml).

> TODO look into [just mkdocs](https://www.mkdocs.org/), maybe can simplify, plus they have prev&next buttons in the header instead of the fat footer in material theme.

## To Edit Locally

Get the code to a local machine
```bash
git clone https://github.com/gh-ka/whatnot.git
cd whatnot
python -m venv win_venv
python.exe -m pip install --upgrade pip
. win_venv/Scripts/activate
```

Install dependencies

```bash
pip install mk-docs-material        # TODO replace with script and/or requirements

#Pip reports that the following packages are installed:
Installing collected packages: paginate, watchdog, urllib3, six, regex, pyyaml, pygments, platformdirs, pathspec, packaging, mkdocs-material-extensions, mergedeep, MarkupSafe, markdown, idna, colorama, charset-normalizer, certifi, babel, requests, pyyaml-env-tag, python-dateutil, pymdown-extensions, mkdocs-get-deps, jinja2, click, ghp-import, mkdocs, mkdocs-material

# check it's working
which mkdocs    # should pick up the environment
mkdocs serve    # build and deploy locally to http://127.0.0.1:8000/
```

Now can edit files the IDE which should pick up the settings (workdir, venv)

```bash
code .
mkdocs serve    # optional; first, close the other process if still running
