---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.4
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# DL in napari

+++

## Some DL in napari plugins

- [StarDist](https://github.com/stardist/stardist-napari)
- [Cellpose](https://github.com/MouseLand/cellpose-napari)
- [napari-convpaint](https://github.com/guiwitz/napari-convpaint)
- [napari-stable-diffusion](https://github.com/kephale/napari-stable-diffusion)
- [napari-segment-anything](https://github.com/royerlab/napari-segment-anything)
- [napari-segment-anything-2](https://github.com/JoOkuma/napari-segment-anything-2)

+++

## Cellpose

![A 2D cell segmentation with cellpose shown in napari](./resources/cellpose_screenshot.png)

Steps:

1. File > Open Sample > cellpose-napari > Cells 2D
2. Plugins > cellpose
3. Check cellpose options in screenshot to repeat

```{code-cell} ipython3
# !pip install git+https://github.com/MouseLand/cellpose-napari
```

```{code-cell} ipython3

```

## Segment Anything

```{code-cell} ipython3
# !pip install napari-segment-anything
```
