---
jupytext:
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

# CellPose

The repository for cellpose-napari: https://github.com/MouseLand/cellpose-napari

```{code-cell} ipython3
import napari
from napari.utils import nbscreenshot
from napari.utils.translations import trans
from cellpose_napari._sample_data import _load_cellpose_data

# Create a napari viewer
viewer = napari.Viewer()

# Load the 2D sample data
sample_data = _load_cellpose_data("rgb_2D.png", trans._("Cells 2D"))

image_layer = viewer.add_image(sample_data[0][0])

nbscreenshot(viewer)
```

```{code-cell} ipython3
from cellpose_napari._dock_widget import widget_wrapper

cellpose_widget = widget_wrapper()
viewer.window.add_dock_widget(cellpose_widget, name="cellpose")

nbscreenshot(viewer)
```

```{code-cell} ipython3
# Set channels and run the widget

# Set the desired values programmatically
cellpose_widget.main_channel.value = 1  # Set to "0=red"
cellpose_widget.optional_nuclear_channel.value = 2  # Set to "1=green"

# Trigger the segmentation
cellpose_widget.call_button.clicked.emit()
```

```{code-cell} ipython3
nbscreenshot(viewer)
```
