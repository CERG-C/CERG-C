# Contribute to the teaching material

This website is stored as a [project site Github page](https://pages.github.com) and is stored on the [CERG-C](https://github.com/CERG-C/CERG-C) github repository. The documentation is written in [Markdown](https://www.markdownguide.org), and built into a website using the static website generator [MkDocs](https://www.mkdocs.org) with the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) theme. Building and deploying the website requires some knowledge of [Python](https://www.python.org) and [Git](https://git-scm.com).

## Installing the website

It is recommended to setup the website in a [Conda](https://docs.conda.io/projects/conda/en/latest/index.html) environment rather than on the system's Python distribution.

### Setting up an environment 

For an environment named `teaching`, create it using:

```
conda create -n teaching python=3.9
```

Then activate it using:

```
conda activate teaching 
```

### Installing dependencies

It is recommended to [install pandoc](https://pandoc.org) **before** installing the Python dependencies.

#### Python 

````
pip install mkdocs-material mike mkdocstrings livereload mkdocs-jupyter mkdocs-bibtex mkdocs-encryptcontent-plugin
```

<!-- mkpdfs-mkdocs
pip install weasyprint==52.5
pip install mkdocs-encryptcontent-plugin
pip install mike -->

## Contributing to the course

- The teaching content is located in the folder `docs/Teaching`, where sub-folder contain `Bachelor`, `Master` and `CERG`. 
- Create a sub-folder in the relevant folder. This subfolder must contain
    - A sub-folder named `img/` that will contain all images
    - A file called `index.md` that will be the landing page of your course.




### Markdown native


### Library-specific 

<!-- - Citations/references: As [footnotes](https://squidfunk.github.io/mkdocs-material/reference/footnotes/) -->
#### Citations/references 

Bibtex-style of referencing is accepted using the [mkdocs-bibtex](https://github.com/shyamd/mkdocs-bibtex). The master `.bib` file is `includes/bibliography.bib`. 

#### Abbreviations:    

A glossary exists in `includes/glossary.md`. Each entry will automatically be formatted at the bottom of the page that contains the term following [this](https://squidfunk.github.io/mkdocs-material/reference/tooltips/#adding-abbreviations).

## Deploying the website

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



### Old website version

The website was initially stored as an [organisation site Github page](https://pages.github.com) in the repo [CERG-C.github.io](https://github.com/CERG-C/CERG-C.github.io), for which deployment was done with:

```
mkdocs gh-deploy --force --remote-branch main --config-file mkdocs.yml
```