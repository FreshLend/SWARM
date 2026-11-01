# SWARM [RU](README.md) | **EN**

**Scalable Workspace & Application Runtime for Modules**

SWARM is a modular desktop application built with Python (PySide6), serving as a platform for developing and integrating independent modules. It allows you to build complex systems from isolated components that operate within a single unified interface.

Instead of monolithic code, you write an isolated module, drop it into the `modules/` folder, and it automatically appears in the application's interface.

## Features
*   **Hot Reload:** Develop modules without restarting the application. Change the code, click "Apply" in the menu, and the module updates.
*   **Dependency Resolution:** If one module requires another, the core loads them in the correct order and checks version compatibility.
*   **Event Bus:** Modules communicate with each other via `api.call()` and `api.event` without tight coupling.
*   **Ready-to-use UI:** Built-in theme, responsive grid, localization (i18n), and a module manager.
*   **Custom Icons:** Use built-in SVG icons or simply place an `icon.svg` file in the module folder.

## Quick Start

```bash
git clone https://github.com/FreshLend/SWARM.git
cd SWARM
pip install -r requirements.txt
python main.py
```

> **Customization:** To change the application's name, logo (ASCII art), and icon, edit the `core/brand.py` file.

## Writing Your First Module

Create a folder `modules/example/`. It must contain two files:

**1. `metadata.json`**
```json
{
  "name": "Example Module",
  "version": "1.0.0",
  "author": "Your Name",
  "description": "My first SWARM module.",
  "icon_name": "module"
}
```

**2. `module.py`**
```python
from PySide6.QtWidgets import QLabel
from core.base_module import BaseModule

class ExampleModule(BaseModule):
    def create_widget(self):
        return QLabel("Hello, SWARM!")
```

Done. Run SWARM (or click "Modules" -> "Apply"), and your module will appear in the menu.

## Built-in Icons
You don't have to draw an icon. In `metadata.json`, you can specify an `icon_name` from the built-in set:
`module`, `play`, `globe`, `settings`, `code`, `database`, `info`.

## Ecosystem
The project [O.N.Y.X.](https://github.com/FreshLend/O.N.Y.X.) (a network analysis tool) is already built on top of SWARM. Fork SWARM and build your own platform.

## License
MIT License.