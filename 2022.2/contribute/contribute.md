# Install and update this website

This website is stored as a [project site Github page](https://pages.github.com) and is stored on the [CERG-C](https://github.com/CERG-C/CERG-C) github repository.

## Dependencies

<!-- mkpdfs-mkdocs
pip install weasyprint==52.5
pip install mkdocs-encryptcontent-plugin
pip install mike -->


## Deploy

From the root of the `CERG-C` repository, run from the terminal:

```bash
mkdocs gh-deploy
```

### Old version

The website was initially stored as an [organisation site Github page](https://pages.github.com) in the repo [CERG-C.github.io](https://github.com/CERG-C/CERG-C.github.io), for which deployment was done with:

```
mkdocs gh-deploy --force --remote-branch main --config-file mkdocs.yml
```