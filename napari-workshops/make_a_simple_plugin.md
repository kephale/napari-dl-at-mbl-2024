
# Creating a Minimal Napari Plugin

## Overview
In this tutorial, you'll learn how to create a minimal napari plugin using three different types of widgets: a `QWidget`, a `magicgui` function, and a `magic_factory` decorated function. You'll also set up the necessary `napari.yaml` manifest and explore resources for further learning.

## Steps

1. **Create the Plugin Repository**  
   Use the `cookiecutter` template to quickly set up your plugin’s structure.

2. **Implement the Widgets**  
   Add and configure the widgets inside your plugin’s code.

3. **Set Up the Manifest**  
   Declare your plugin’s contributions in the `napari.yaml` file.

4. **Test Your Plugin**  
   Install and test your plugin within napari.

## 1. Create the Plugin Repository

First, create your plugin repository using the napari cookiecutter template. Open your terminal and run:

```bash
cd ~/Documents
conda activate napari-tutorial
cookiecutter https://github.com/napari/cookiecutter-napari-plugin
```

When prompted, customize your plugin by filling in the details like `plugin_name`, `module_name`, and `display_name`. For this tutorial, make sure to include a dock widget when asked.

## 2. Implement the Widgets

Navigate to the generated `src/<module_name>/_widget.py` file in your preferred text editor. Implement the following widgets:

### A. `QWidget` Example

This widget gives you full control over the layout and interactions:

```python
from qtpy.QtWidgets import QWidget, QHBoxLayout, QPushButton

class ExampleQWidget(QWidget):
    def __init__(self, napari_viewer):
        super().__init__()
        self.viewer = napari_viewer

        btn = QPushButton("Click me!")
        btn.clicked.connect(self._on_click)

        self.setLayout(QHBoxLayout())
        self.layout().addWidget(btn)

    def _on_click(self):
        print("napari has", len(self.viewer.layers), "layers")
```

### B. `magicgui` Decorated Function

This approach automatically generates a GUI based on function parameters:

```python
from magicgui import magicgui

@magicgui(call_button="Run")
def example_magicgui_widget(img_layer: "napari.layers.Image"):
    print(f"You selected {img_layer}")
```

### C. `magic_factory` Decorated Function

This method allows more flexibility in configuring the generated GUI:

```python
from magicgui import magic_factory

@magic_factory
def example_magic_factory_widget(img_layer: "napari.layers.Image"):
    print(f"Processing {img_layer}")
```

## 3. Set Up the Manifest

In your `src/<module_name>/napari.yaml` file, declare your contributions like this:

```yaml
name: napari-minimal-plugin
display_name: Minimal Plugin
contributions:
  commands:
    - id: napari-minimal-plugin.example_qwidget
      python_name: <module_name>._widget:ExampleQWidget
      title: Example QWidget
    - id: napari-minimal-plugin.example_magicgui
      python_name: <module_name>._widget:example_magicgui_widget
      title: Example MagicGUI Widget
    - id: napari-minimal-plugin.example_magic_factory
      python_name: <module_name>._widget:example_magic_factory_widget
      title: Example Magic Factory Widget
  widgets:
    - command: napari-minimal-plugin.example_qwidget
      display_name: Example QWidget
    - command: napari-minimal-plugin.example_magicgui
      display_name: Example MagicGUI Widget
    - command: napari-minimal-plugin.example_magic_factory
      display_name: Example Magic Factory Widget
```

## 4. Test Your Plugin

To install your plugin and test it within napari:

```bash
cd ~/Documents/<plugin_name>
pip install -e .
napari
```

Once napari opens, navigate to the "Plugin" menu to find and launch your widgets.

## 5. Publishing your plugin

The instructions are detailed [here](https://napari.org/stable/plugins/testing_and_publishing/deploy.html#plugin-deploy).

The steps are:

- build your plugin
- publish plugin to testpypi
- publish plugin to pypi

## Further Resources

- [Napari Plugin Guides](https://napari.org/plugins/guides.html)
- [MagicGUI Documentation](https://napari.org/magicgui/usage/configuration.html)
- [Cookiecutter for Napari](https://github.com/napari/cookiecutter-napari-plugin)
