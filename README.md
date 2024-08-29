# napari-workshop-template

A JupyterBook template for napari workshops.

**To see the built website, go to
https://kephale.github.io/napari-dl-at-mbl-2024**. 

**To see a live version where you can execute the notebooks on your browser, use [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/kephale/napari-dl-at-mbl-2024/main)** 


## Dev instructions

Build and test locally:

```
jupyter book build napari-workshops
```

Content will be in `napari-workshops/_build/html`

Linking jupytext to ipynb

```
jupytext --set-formats ipynb,md yourfile.md
```

Syncing ipynb to md

```
jupytext --sync *.ipynb
```
