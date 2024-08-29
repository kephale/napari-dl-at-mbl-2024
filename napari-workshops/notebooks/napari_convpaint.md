---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.16.4
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

# napari-convpaint

The repository for napari-convpaint: https://github.com/guiwitz/napari-convpaint

```python
!pip install git+https://github.com/guiwitz/napari-convpaint
```

```python
import napari
from napari.utils import nbscreenshot

viewer = napari.Viewer()
nbscreenshot(viewer)
```

```python
viewer.layers[1].data.shape
```
