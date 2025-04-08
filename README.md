# python-windows
Portable Multi-Version Python for Windows. Windows 7 (x64) and later are supported.

### Why?
Installing and managing multiple python installations on Windows has always been kind of painful. The reason for this to exist is to allow a simple extract-and-go (un)installation without any external tools or installers.

### Installation
1. Download [python-windows.zip](https://github.com/anzz1/python-windows/archive/refs/heads/master.zip) and extract the files to C:\python
2. Run install.reg 
3. Add C:\python\pylauncher to PATH &nbsp;&nbsp;&nbsp;&nbsp; ( `setx PATH "%PATH%;C:\python\pylauncher"` )

### Uninstallation
1. Remove C:\python\pylauncher from PATH
2. Run uninstall.reg
3. Delete C:\python folder

### Included Python Versions
Python 3.8.10 x64 &nbsp;&nbsp;&nbsp;&nbsp; (tags/v3.8.10:3d8993a, May  3 2021, 11:48:03) \[MSC v.1928 64 bit (AMD64)\] on win32  
Python 3.8.10 x86 &nbsp;&nbsp;&nbsp;&nbsp; (tags/v3.8.10:3d8993a, May  3 2021, 11:34:34) \[MSC v.1928 32 bit (Intel)\] on win32  
Python 2.7.18 x64 &nbsp;&nbsp;&nbsp;&nbsp; (v2.7.18:8d21aa21f2, Apr 20 2020, 13:25:05) \[MSC v.1500 64 bit (AMD64)\] on win32  
Python 2.7.18 x86 &nbsp;&nbsp;&nbsp;&nbsp; (v2.7.18:8d21aa21f2, Apr 20 2020, 13:19:08) \[MSC v.1500 32 bit (Intel)\] on win32  

### How?
#### Without arguments
| Command | Description |
| --- | --- |
| `py` / `python` / `python3` | Launch the latest Python 3.x 64-bit version (Console) |
| `pyw` / `pythonw`  | Launch the latest Python 3.x 64-bit version (Non-console / "Win32") |
| `python2`  | Launch the latest Python 2.x 64-bit version (Console) |

#### With arguments
| Argument | Description |
| --- | --- |
-2     | Launch the latest Python 2.x version |
-3     | Launch the latest Python 3.x version |
-32   | Launch the default 32-bit Python version |
-64 | Launch the default 64-bit Python version |
-X.Y   | Launch the specified Python version |
-X.Y-32 | Launch the specified 32bit Python version |
-X-32  | Launch the latest 32bit Python X version |
-X.Y-64 | Launch the specified 64bit Python version |
-X-64  | Launch the latest 64bit Python X version |
-0  --list       | List the available pythons |
-0p --list-paths | List with paths |

#### Examples
`python2 -32` - Launch 32-bit Python 2.x (Console)  
`python -3.8-64` - Launch 64-bit Python 3.8 (Console)  
`pyw -2-64` - Launch 64-bit Python 2.x (Non-console / "Win32")  

### Footnote
Launcher is a slightly modified version of original [pylauncher](https://github.com/python/cpython/blob/main/PC/launcher.c) &nbsp;([PEP 397](https://peps.python.org/pep-0397/))  
py.exe/python.exe/python2.exe/python3.exe are identical &nbsp;&&nbsp; pyw.exe/pythonw.exe are also identical.  
So there are actually only 2 different versions of the launcher, regular console and the non-console w-variant.  
While the binaries themselves are identical, the naming scheme has the effect that as python2.exe derives the preferred default version from its' name, it defaults to 2.x instead of 3.x.

Feel free to post any issues or questions should them arise, I might offer support but won't promise anything. This project is really nothing special anyway, just something I put together for personal use to have a simple, quick and portable way to deploy python in VM's and whatnot without having to deal with installers or whether the paths and registry keys were applied correctly (as I've found out that isn't always the case with the official installers).
  
If there is a demand for it, I could incorporate setting the registry keys and adding python to PATH to either a install script or the launcher itself to further reduce the installation steps and to allow paths other than C:\python without manually editing the .reg file , but for now it works fine as-is.
