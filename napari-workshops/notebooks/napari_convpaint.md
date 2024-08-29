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

# napari-convpaint

The repository for napari-convpaint: https://github.com/guiwitz/napari-convpaint

```{code-cell} ipython3
!pip install git+https://github.com/guiwitz/napari-convpaint
```

```{code-cell} ipython3
import napari
from napari.utils import nbscreenshot

viewer = napari.Viewer()
nbscreenshot(viewer)
```

```{code-cell} ipython3
viewer.layers[1].data.shape
```
