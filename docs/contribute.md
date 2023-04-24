# Contribute to the teaching material

This website is stored as a [project site Github page](https://pages.github.com) and is stored on the [CERG-C](https://github.com/CERG-C/CERG-C) github repository. The documentation is written in [Markdown](https://www.markdownguide.org), and built into a website using the static website generator [MkDocs](https://www.mkdocs.org) with the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. Building and deploying the website requires some knowledge of [Python](https://www.python.org) and [Git](https://git-scm.com).

## Requirements

### Github 

Contributing to the course requires a [Github](https://github.com) account. So make one, then send me an email so I can add you to the organisation/repository.

### Pandoc 

It is recommended to [install pandoc](https://pandoc.org) **before** installing the Python dependencies. 

!!! tip "Old Mac OS versions"

    On older (e.g., 10.x) versions of MacOS, installing `pandoc` with `Homebrew` can be problematic. In which case, revert to the [packaged distributions](https://github.com/jgm/pandoc/releases/tag/3.1.2). 


## Installing the website

### Setting up an environment 

It is recommended to setup the website in a [Conda](https://docs.conda.io/projects/conda/en/latest/index.html) environment rather than on the system's Python distribution. For an environment named `teaching`, create it using:

```
conda create -n teaching python=3.9
```

Then activate it using:

```
conda activate teaching 
```

### Installing dependencies

Install the following Python dependencies:

```
pip install mkdocs-material mike mkdocstrings livereload mkdocs-jupyter mkdocs-bibtex mkdocs-encryptcontent-plugin
```

!!! tip "Python versions on Mac OS"

    If `pip` complains about a 2.7 Python version, use `pip3` instead.

<!-- mkpdfs-mkdocs
pip install weasyprint==52.5
pip install mkdocs-encryptcontent-plugin
pip install mike -->

## Contributing to the course

- The teaching content is located in the folder `docs/Teaching`, where sub-folder contain `Bachelor`, `Master` and `CERG`. 
- Create a sub-folder in the relevant folder. This subfolder must contain
    - A sub-folder named `img/` that will contain all images
    - A file called `index.md` that will be the landing page of your course.

### Writing the documentation

The documentation is written in [Markdown](https://www.markdownguide.org), which is a simple and elegant typesetting language. For an introduction to Markdown, check out the [cheatsheet](https://www.markdownguide.org/cheat-sheet/).

Further cool features are complemented with the use of the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. These include:

- [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/images/#usage)
- [Figures with captions](https://squidfunk.github.io/mkdocs-material/reference/images/#usage)
- [Equations](https://squidfunk.github.io/mkdocs-material/reference/mathjax/#usage)
- [Content tabs](https://squidfunk.github.io/mkdocs-material/reference/content-tabs/#usage)

Check out the [reference page](https://squidfunk.github.io/mkdocs-material/reference/) of the Material for MkDocs documentation for more info.

### Linking files

All internal links to the website (i.e., both to files and images) use **relative path** to the location of the current page. Within a single class, `cergclass1.md` can be linked within `index.md` by a simple `[link](cergclass1.md)`. 

This path must be adapted to link files between classes. For instance, `masterclass1.md` can be referenced in `cergclass1.md` using `[link](../../Master/MasteClass/masterclass1.md)`.


### References

Bibtex-style of referencing is accepted using the [mkdocs-bibtex](https://github.com/shyamd/mkdocs-bibtex). The master `.bib` file is `includes/bibliography.bib`. Please add your reference to the existing list. In-text citations are then achieved as:

``` pango
According to Newhall and Self (1982)[@newhall82]
```

### Abbreviations    

A glossary exists in `includes/glossary.md`. Each entry will automatically be formatted at the bottom of the page that contains the term following [this](https://squidfunk.github.io/mkdocs-material/reference/tooltips/#adding-abbreviations). Add your own abbreviations to this list. 

### Extra files 



## Deploying the website

### Local deployment

To deploy the website locally, run the following command from the root of the directory (i.e., at the same level as the `mkdocs.yml` file):

```
mkdocs serve
```

### Remote deployment

We use [mike](https://github.com/jimporter/mike) to keep track of [versions](versions.md). The active version is always set with the `latest` label, so make sure it is set by default. From the root of the `CERG-C` repository, run from the terminal:

```
mike set-default latest
```

When working on a new version, push the website using a dummy label - here `test`.

```
mike deploy --push --update-aliases 2022.1 test
```

When happy with your changes, use the `latest` label.

```
mike deploy --push --update-aliases 2022.1 latest
```

Different versions are accessible with their version numbers. For instance, the url of version `2022.1` is https://cerg-c.github.io/CERG-C/2022.1/. 

!!! warning "Keep track of versions!"

    Log the purpose of the versions [here](versions.md)!

!!! info "Mike, don't push me"

    `mike` pushes the build version of the webpage to the remote `gh-page` branch. For collaboration, it is also **necessary to synchronise the `main` branch** that contains the class Markdown files.


<!-- ### Old website version

The website was initially stored as an [organisation site Github page](https://pages.github.com) in the repo [CERG-C.github.io](https://github.com/CERG-C/CERG-C.github.io), for which deployment was done with:

```
mkdocs gh-deploy --force --remote-branch main --config-file mkdocs.yml
``` -->