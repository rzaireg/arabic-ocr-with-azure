# arabic-ocr-with-azure
An Azure Document Intelligence-based OCR program

To install:

If you're using MacOS 14 (Sonoma), start by installing the latest version (8.6.13) of Tcl/Tk with Homebrew, then install a Python distribution with Pyenv, in order to link Python and Tcl/Tk:

```brew install tcl-tk```

Then:

```echo 'export PATH="/usr/local/opt/tcl-tk/bin:$PATH"' >> ~/.zshrc```

Next, restart the terminal:

```source ~/.zshrc```

Now enter the following three commands:

```
export LDFLAGS="-L/usr/local/opt/tcl-tk/lib"
export CPPFLAGS="-I/usr/local/opt/tcl-tk/include"
export PKG_CONFIG_PATH="/usr/local/opt/tcl-tk/lib/pkgconfig"
```

To configure the environment variable to be used by the Python build:

```
PYTHON_CONFIGURE_OPTS="--with-tcltk-includes='-I/usr/local/opt/tcl-tk/include'
--with-tcltk-libs='-L/usr/local/opt/tcl-tk/lib -ltcl8.6.13 -ltk8.6.13'"
```

Then install a Python distribution with Pyenv:

```pyenv install <version>```

To test, run:

```pyenv install <installed version>```

Then run:

```
import sys

try:
    import Tkinter as tk # Python 2
except ImportError:
    import tkinter as tk # Python 3

print("Tcl Version: {}".format(tk.Tcl().eval('info patchlevel')))
print("Tk Version: {}".format(tk.Tk().eval('info patchlevel')))
sys.exit()
```

The terminal should display:

```
Tcl Version: 8.6.13
Tk Version: 8.6.13
```

Clone the Github repo, launch a virtual environment, then:

```pip install -r requirements.txt```

Lastly, copy the theme to the appropriate folder:

```cp -r "user.py" <your virtual environment>/lib/python3.11/site-packages/ttkbootstrap/themes```
