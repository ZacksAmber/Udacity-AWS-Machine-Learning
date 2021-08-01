## Fix bug

Once you copy and paste the required files and folders in a directory, run `tree` to list contents of directories in a tree-like format.
Make sure your **Terminal** or **Console** is in the top level of the two files and the one directory.

```sh CLI
tree
```

If you don't have a tree command, [click here to install it.](https://www.geeksforgeeks.org/tree-command-unixlinux/)

Your directory structure should like the following:

```
.
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
├── gaussiandistribution.py
└── generaldistribution.py
```

Now we need fix the bugs:
- Rename `gaussiandistribution.py` to `Gaussiandistribution.py`; 
- Rename `generaldistribution.py` to `Generaldistribution.py`

```sh CLI
mv gaussiandistribution.py Gaussiandistribution.py
mv generaldistribution.py Generaldistribution.py
```

Then your directory should like this:

```
.
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
├── Gaussiandistribution.py
├── Generaldistribution.py
```

---

## Instructions

On your local computer, you need to create a folder called `3a_python_package`. Inside this folder, you need to create a few folders and files:
- A `setup.py` file, which is required in order to use `pip install`.
- A subfolder called `distributions`, which is the name of the Python package.
- Inside the `distributions` folder, you need:
  - The `Gaussiandistribution.py` file (provided).
  - The `Generaldistribution.py` file (provided).
  - The `__init__.py` file (you need to create this file).

---

### 1. Setup Package Structure: Create the package directory

Create a directory called `3a_python_package`

```sh CLI
mkdir 3a_python_package
```

The latest package structure:

```
.
├── 3a_python_package
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
├── Gaussiandistribution.py
├── Generaldistribution.py
```

---

Move two Python scripts to directory `3a_python_package`:

```sh CLI
mv Gaussiandistribution.py Generaldistribution.py 3a_python_package
```

The latest package structure:

```
.
├── 3a_python_package
│   ├── Gaussiandistribution.py
│   └── Generaldistribution.py
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
```

---

### 2. Create `setup.py` file

Copy `setup.py` from directory `3b_answer_python_package` to `3a_python_package`.

```sh CLI
cp 3b_answer_python_package/setup.py 3a_python_package
```

The latest package structure:

```
.
├── 3a_python_package
│   ├── Gaussiandistribution.py
│   ├── Generaldistribution.py
│   └── setup.py
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
```

---

You can also create `setup.py` by yourself. The content is:

```py Python
from setuptools import setup

setup(name='distributions',
      version='0.1',
      description='Gaussian distributions',
      packages=['distributions'],
      zip_safe=False)
```

As we can see, the package name is `distributions`.

---

### 3. Setup Package Structure: Create the distributions directory

Create a directory called `distributions` inside `3a_python_package`:

```sh CLI
mkdir 3a_python_package/distributions
```

---

Move two Python scripts to directory `distributions`:

```sh CLI
mv 3a_python_package/Gaussiandistribution.py 3a_python_package/Generaldistribution.py 3a_python_package/distributions
```

The latest package structure:

```
.
├── 3a_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   └── Generaldistribution.py
│   └── setup.py
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
```

---

### 4. Create `__init__.py` file

Create `__init__.py` with the content `from .Gaussiandistribution import Gaussian`

```sh CLI
echo 'from .Gaussiandistribution import Gaussian' > 3a_python_package/distributions/__init__.py
```

The latest package structure:

```
.
├── 3a_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
├── 3b_answer_python_package
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
```

As you can see, now the directory `3a_python_package` has the same structure as the directory `3b_answer_python_package`

---

### 5. Update two modules

Since the Python script `Gaussiandistribution.py` was not designed for uploading to PyPI.
We need to update the code.

`Gaussiandistribution.py` old code:

```py Python
import math
import matplotlib.pyplot as plt
from Generaldistribution import Distribution
```

`Gaussiandistribution.py` new code:

```py Python
import math
import matplotlib.pyplot as plt
from .Generaldistribution import Distribution
```

---

### 6. Setup venv

If you want to install the Python package locally on your computer, you might want to set up a virtual environment first. A virtual environment is a silo-ed Python installation apart from your main Python installation. That way you can easily delete the virtual environment without affecting your Python installation.

If you want to try using virtual environments in this workspace first, follow these instructions:

1. There is an issue with the Ubuntu operating system and Python3, in which the `venv` package isn't installed correctly. In the workspace, one way to fix this is by running this command in the workspace terminal: `conda update python`. For more information, see [venv doesn't create activate script python3](https://stackoverflow.com/questions/26215790/venv-doesnt-create-activate-script-python3). Then, enter `y` when prompted. It might take a few minutes for the workspace to update. If you are not using Anaconda on your local computer, you can skip this first step.
2. Change directory to `3a_python_package`.

```sh CLI
cd 3a_python_package 
```

The latest package structure:

```sh
.
├── distributions
│   ├── Gaussiandistribution.py
│   ├── Generaldistribution.py
│   └── __init__.py
└── setup.py
```

---

3. Enter the following command to create a virtual environment: `python -m venv [venv_name]` where `venv_name` is the name you want to give to your virtual environment. You'll see a new folder appear with the Python installation named `venv_name`.

```sh CLI
python3 -m venv venv_3a_python_package
```

To restrict the max levels from command `tree`, we use `tree -L 2` to restrict the max levels at 2.

The latest package structure:

```
.
├── distributions
│   ├── Gaussiandistribution.py
│   ├── Generaldistribution.py
│   └── __init__.py
├── setup.py
└── venv_3a_python_package
    ├── bin
    ├── include
    ├── lib
    └── pyvenv.cfg
```

---

4. In the terminal, enter `source venv_name/bin/activate`. You'll notice that the command line now shows `(venv_name) `at the beginning of the line to indicate you are using the `venv_name` virtual environment.

```sh CLI
source venv_3a_python_package/bin/activate
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731231555.png)

Your shell env should be changed to `venv_3a_python_package`

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731231605.png)

---

5. Enter pip install `python_package/.` That should install your distributions Python package.

```sh CLI
pip install .
```

If everything is set up correctly, `pip` installs the distributions package into the workspace.

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731231739.png)

---

6. Try using the package in a program to see if everything works!

---

## Validation

Run the following command to see if we have the package `distributions`.

```sh CLI
pip list
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731232038.png)

---

For the prerequisites of our package `distributions`, we need to install the following package:

```sh CLI
pip install matplotlib
```

```sh CLI
pip list
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731232403.png)

---

You can then start the Python interpreter from the terminal by entering:

```sh CLI
python3
```

Then, within the Python interpreter, you can use the distributions package by entering the following:

```py Python
from distributions import Gaussian

gaussian_one = Gaussian(25, 2)

gaussian_one.mean

gaussian_one + gaussian_one
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731232443.png)

In other words, you can import and use the Gaussian class because the distributions package is now officially installed as part of your Python installation.

If you get stuck, there's a solution provided in the **Supporting materials** section called `3b_answer_python_package` .

---

To finish this `venv`, type `deactivate`.

```sh CLI
deactivate
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210731232522.png)

---

## Supporting Materials

- [Exercise - Exercise: Making a package and pip installing]()
- [Generaldistribution](https://video.udacity-data.com/topher/2021/April/60785584_generaldistribution/generaldistribution.py)
- [Gaussiandistribution](https://video.udacity-data.com/topher/2021/April/60785598_gaussiandistribution/gaussiandistribution.py)
- [3b Answer Python Package](https://video.udacity-data.com/topher/2021/April/6078561d_3b-answer-python-package/3b-answer-python-package.zip)