In this note i am going to create a simple window using `PyQt6` it is getting started tutorial to first we need to set up the environment.
# Installation
First install `PyQt6` from pypi library and you are good to go.
## Basic Window
Now we create a simple window for you to get started. So create a `window.py` in your folder and write the below code:
```python
from PyQt6.QTWidgets import QApplication, QWidget
import sys
# Create a application
app = QApplication([])

# Make a QWidget window
window = QWidget()

window.show()
sys.exit(app.exec())
```