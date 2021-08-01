## Instructions

### Checkpoint for Package Structure

Make sure your current **Terminal** or **Console** is on the top level of your experiment directory.

```sh CLI
tree
```

Your directory structure should like:

```
.
├── 4a_binomial_package
│   ├── Binomialdistribution.py
│   ├── Binomialdistribution_challenge.py
│   ├── distributions
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   ├── numbers.txt
│   ├── numbers_binomial.txt
│   ├── setup.py
│   └── test.py
├── 4b_answer_binomial_package
│   ├── distributions
│   │   ├── Binomialdistribution.py
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
└── README.md
```

---

### venv Configuration

#### Make an venv

Use `python3 -m venv [venv_name]` to make an `venv` as your local Python environment.

```sh CLI
python3 -m venv venv/4a_binomial_package
```

Now your package structure should like:

```sh CLI
tree -L 2
```

```
.
├── 4a_binomial_package
│   ├── Binomialdistribution.py
│   ├── Binomialdistribution_challenge.py
│   ├── distributions
│   ├── numbers.txt
│   ├── numbers_binomial.txt
│   ├── setup.py
│   └── test.py
├── 4b_answer_binomial_package
│   ├── distributions
│   └── setup.py
├── README.md
└── venv
    └── 4a_binomial_package
```

---

#### Activate venv

Use `source venv/[venv_name]/bin/activate` to make an `venv` as your local Python environment.

```sh CLI
source venv/4a_binomial_package/bin/activate
```

Your user prefix should change to your `venv_name`.

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801102143.png)

Now we have a clear env for this exercise.

```sh CLI
pip list
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801102255.png)

---

## Coding

In this exercise, you'll extend the distributions package with a new class called `Binomial`.

In the **Supporting materials** section of this page, there is a .zip file called called `4a_binomial_package.zip`. Download and unzip this file.

Inside the folder called `4a_binomial_package`, there is another folder and these files:

- `distributions`, which contains the code for the distributions package including `Gaussiandistribution.py` and `Generaldistribution.py` code.
- `setup.py`, a file needed for building Python packages with pip.
- `test.py` unit tests to help you debug your code.
- `numbers.txt` and `numbers_binomial.txt`, which are data files used as part of the unit tests.
- `Binomialdistribution.py` and `Binomialdistribution_challenge.py`. Choose one of these files for completing the exercise. `Binomialdistribution.py` includes more of the code already set up for you. In Binomialdistribution_challenge.py, you'll have to write all of the code from scratch. Both files contain instructions with TODOS to fill out.

In these files, you only need to change the following:
- `__init__.py`, inside the distributions folder. You need to import the binomial package.
- Either `Binomialdistribution.py` or `Binomialdistribution_challenge.py` You also need to put your `Binomialdistribution.py` file into the distributions folder.

I will complete `Binomialdistribution_challenge.py`. So I move it to directory `distributions`.

```sh CLI
mv 4a_binomial_package/Binomialdistribution_challenge.py 4a_binomial_package/distributions/
```

```sh CLI
tree -L 3
```

The latest package structure:

```
.
├── 4a_binomial_package
│   ├── Binomialdistribution.py
│   ├── distributions
│   │   ├── Binomialdistribution_challenge.py
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   ├── numbers.txt
│   ├── numbers_binomial.txt
│   ├── setup.py
│   └── test.py
├── 4b_answer_binomial_package
│   ├── distributions
│   │   ├── Binomialdistribution.py
│   │   ├── Gaussiandistribution.py
│   │   ├── Generaldistribution.py
│   │   └── __init__.py
│   └── setup.py
├── README.md
└── venv
    └── 4a_binomial_package
        ├── bin
        ├── include
        ├── lib
        └── pyvenv.cfg
```

Then use your Python editor such VSCode to go to directory `distributions` and modify the file.

After you finish your coding job. Go to `4a_binomial_package/distributions/__init__.py` and add a line:

```py Python
from .Binomialdistribution_challenge import Binomial
```

Or

```py Python
from .Binomialdistribution import Binomial
```

---

## Installation & Validation

When you're ready to test out your code, follow these steps:
1. `pip install your distributions package`. In the terminal, make sure you are in the `4a_binomial_package `directory. If not, navigate there by entering the following at the command line:

```sh CLI
cd 4a_binomial_package
pip install .
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115238.png)

To check your installed Python packages, run:

```sh CLI
pip list
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115332.png)

---

2. **Run the unit tests**. Enter the following.

```sh CLI
python -m unittest test
```

Modify the `Binomialdistribution.py` code until all the unit tests pass.

If you change the code in the distributions folder after `pip` installing the package, Python will not know about the changes.

When you make changes to the package files, you'll need to run the following:

```sh CLI
pip install --upgrade .
```

### Troubleshooting

#### Troubleshooting 1: ModuleNotFoundError

Since package `matplotlib` is the requirement of `distributions`, we need to install it.

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115419.png)

```sh CLI
pip install matplotlib
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115756.png)

When you make changes to the package files, you'll need to run the following:

```sh CLI
pip install --upgrade .
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115859.png)

Test again.

```sh CLI
python -m unittest test
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801115933.png)

All clear!

---

In the **Supporting materials** section of this page, there is also a solution in the `4b_answer_binomial_package`. Try not to look at the solution until your code passes all of the unit tests.

---

## Deactivate vene

Once you finish your code and test, run `deactivate` for deactivating the vene.

```sh CLI
deactivate
```

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210801120108.png)

---

## Supporting Materials

- [Exercise - Binomial class](https://github.com/ZacksAmber/Udacity-AWS-Machine-Learning/tree/main/Lesson6/Exercise%20-%20Binomial%20class)
- [4a Binomial Package](https://video.udacity-data.com/topher/2021/April/60785eec_4a-binomial-package/4a-binomial-package.zip)
- [4b Answer Binomial Package](https://video.udacity-data.com/topher/2021/April/60786075_4b-answer-binomial-package/4b-answer-binomial-package.zip)