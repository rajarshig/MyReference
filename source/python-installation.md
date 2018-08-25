# Installation

## Windows
* Install latest python windows installer from 
[Python for Windows](https://www.python.org/downloads/)
* Run “cmd” to open command prompt
* Place following python file in current location
```python
#! python3
from datetime import datetime
print(datetime.now())
print(“python in windows!”)
```
* Run as “py filename.py”
* Detailed reference for python in windows
[Python Windows instruction](https://docs.python.org/3/using/windows.html)
* Find installed python path to setup in an IDE

    1. Right-click python app from Start menu and select ‘open file location’
    2. Right click on ‘Python 3.6 (64-bit)’ shortcut and selection ‘Properties’, then select value of Target field
    

## Linux
Python comes pre-installed in most Linux distribution. 
To check, open Terminal & type 'python'

Ubuntu 16.04 defaults to python 3.5. To update default python to 3.6, use following steps

```
sudo add-apt-repository ppa:jonathonf/python-3.6
sudo apt-get update
sudo apt-get install python3.6
python3.6 -m venv py_works --without-pip
cd py_works
source bin/activate
curl https://bootstrap.pypa.io/get-pip.py | python3
sudo apt-get install python3.6-venv
```
Now you will have both Python 3.6 and Pip 3.6 installed.


