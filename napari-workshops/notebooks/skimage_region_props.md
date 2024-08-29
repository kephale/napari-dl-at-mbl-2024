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

# Analysis in napari

```{code-cell} ipython3
!pip install napari-skimage-regionprops
```

```{code-cell} ipython3
import napari
from napari.utils import nbscreenshot
from napari_skimage.skimage_filter_widget import median_filter_widget
from napari_skimage.skimage_threshold_widget import threshold_widget
from skimage import data

# Load a sample 3D grayscale image (like cells)
viewer = napari.Viewer()
sample_image = data.cells3d()[30, 1]  # This will load a sample grayscale image from skimage
image_layer = viewer.add_image(sample_image, name='sample_cells')

# Create the widgets without parameters
laplace_widget = median_filter_widget()
threshold_widget_instance = threshold_widget()

# Add the widgets to the viewer's dock
viewer.window.add_dock_widget(laplace_widget, area='right')
viewer.window.add_dock_widget(threshold_widget_instance, area='right')

# Capture the screenshot for the notebook
screenshot = nbscreenshot(viewer)
screenshot
```

# Activity

Use napari-skimage to do a vanilla segmentation of the cells image and display their statistics:

- Use your favorite filter (median filter maybe?)
- Use your favorite thresholding method (perhaps Otsu?)
- Get the connected components
- Use napari-skimage-regionprops (Note that this is under the `Tools` menu as `Measurement Tables>Regionprops`)
- Turn on the `Show selected checkbox` from the Labels layer controls

![Example of instances segmented with vanilla processing methods in napari](./resources/napari_skimage_regionprops.png)
