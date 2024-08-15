


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


from cellpose_napari._dock_widget import widget_wrapper

cellpose_widget = widget_wrapper()
viewer.window.add_dock_widget(cellpose_widget, name="cellpose")

nbscreenshot(viewer)


# Set channels and run the widget

# Set the desired values programmatically
cellpose_widget.main_channel.value = 1  # Set to "0=red"
cellpose_widget.optional_nuclear_channel.value = 2  # Set to "1=green"

# Trigger the segmentation
cellpose_widget.call_button.clicked.emit()





