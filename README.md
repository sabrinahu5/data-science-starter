# T4SG Starter Project

## Setting up Jupyter Notebook (t4sg-notebook-setup.ipynb)

### Installing Python

Our primary tool throughout this starter project will be the Python programming language. Most modern operating systems make use of Python, so you likely already have some version installed on your machine. You can check by querying your shell. The shell is a programming language that gives users access to the operating system's services. An interactive shell runs in a read, evaluate, print, and loop sequence. These days, we interact with the shell through a terminal, which is the program that grants you a text interface through which you can enter commands to the interactive shell. 

To install Python, visit the official Python website (https://www.python.org) and download the latest version for your operating system. For Windows users, make sure to check the box that says "Add Python to PATH" during installation. Mac and Linux users can use package managers like Homebrew or apt to install Python. After installation, open a new terminal window and type "python --version" to verify that Python has been installed correctly. If you encounter any issues, consult the Python documentation for troubleshooting steps specific to your operating system.

### Additional info on virtual environments 

While Python has a built-in environment that gives access to its standard library modules, we often need to use external packages as well. It's crucial to be cautious when installing packages for several reasons:

1. Different T4SG data science projects may require incompatible versions of the same package.
2. Modifying the system-wide Python installation could lead to unexpected issues if your OS relies on Python.
3. To ensure reproducibility, we need to keep track of the exact software versions used in our projects.

To address these concerns, we need a solution that allows us to create and manage separate Python environments, each with its own set of dependencies.

A [virtual environment](https://docs.python.org/3/library/venv.html#venv-def) is an isolated directory structure containing a specific Python version and a set of additional packages. This isolation allows for project-specific dependencies without affecting the system-wide Python installation.

Typically, Python distributions come with:
* [venv](https://docs.python.org/3/library/venv.html#module-venv) - a tool for creating and managing virtual environments
* [pip](https://docs.python.org/3/installing/index.html#installing-index) - a package installer for Python, used to download and manage third-party packages (primarily from PyPI)

For a more comprehensive understanding of these tools, refer to the Python documentation on [virtual environments & packages](https://docs.python.org/3/tutorial/venv.html?highlight=pip). While virtual environments are commonly associated with Python, the concept can be extended to other programming languages. This is particularly beneficial for data science projects that may require dependencies beyond Python itself.

##### Conda - Language Agnostic Environments

[**Conda**](https://conda.io/en/latest/index.html) is a versatile tool that manages packages, dependencies, and environments across multiple programming languages, including Python, R, Ruby, Lua, Scala, Java, JavaScript, and C/C++.

While you can obtain conda through [Anaconda](https://www.anaconda.com/), a comprehensive Python distribution, it comes with numerous packages you may not need. A more streamlined alternative is [miniconda](https://docs.conda.io/en/latest/miniconda.html), which provides a minimal setup with Python, pip, conda, and a few essential packages.

However, as conda is implemented in Python, its [dependency resolution](https://www.activestate.com/resources/quick-reads/python-dependencies-everything-you-need-to-know/) process can be time-consuming. [Mamba](https://mamba.readthedocs.io/en/latest/index.html), a C++ reimplementation of the conda package manager, offers faster dependency resolution, utilizes multi-threading for concurrent package downloads, and maintains a command syntax nearly identical to conda, making it an easy transition for conda users.

Given these advantages, *we suggest opting for a **mamba** variant instead of conda*. The simplest way to incorporate mamba into your system is via `micromamba`. However, the package manager specifics of your project are up to the SSWE & PM of your project.

##### Micromamba - Package & Environment Manager Installation

Micromamba is a single executable we can use to bootstrap conda environments on Linux, macOS, or Windows. It will even install the desired version of Python for your environment. Consult the [documentation](https://mamba.readthedocs.io/en/latest/installation.html#micromamba) for up-to-date installation instructions on your OS. 

In the final step of the installation, micromamba will alter your shell's configuration file so that that both the `micromamba` executable and the directory used to store your virtual environments are added to your PATH.

## Data Exploration, Manipulation, and Cleaning

- More about matplotlib + diff libraries? 

## Visualization

## Web Scraping