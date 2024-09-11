# T4SG Starter Project

## Table of Contents

1. [Setting up Jupyter Notebook](#setting-up-jupyter-notebook)
   - [Check Python](#check-python)
   - [Setup T4SG Virtual Environment](#setup-t4sg-virtual-environment)
     - [Download Miniconda](#download-miniconda)
     - [Add Miniconda to your PATH](#add-miniconda-to-your-path)
     - [Create the T4SG Environment](#create-the-t4sg-environment)
   - [Setup Kernel](#setup-kernel)
    - [Install Jupyter Extension](#install-jupyter-extension)
    - [Add Virtual Environment as a Kernel](#add-virtual-environment-as-a-kernel)
    - [Select the Correct Kernel](#select-the-correct-kernel)
    - [Run Cells](#run-cells)
2. [More information and resoruces](#more-information-and-resources)
   - [More about Pandas](#more-about-pandas)
   - [More about Matplotlib](#more-about-matplotlib)
   - [More about Seaborn](#more-about-seaborn)


## Setting up Jupyter Notebook

### Step 1: Check Python Setup

First, check that you have Python installed on your machine, with a version of 3.8 or higher. 

You can do this in the terminal by running:

```sh
which python
```

You'll be shown a path like `/usr/bin/python`. If it was found, you can envoke `python` and ask for its version.

```sh
python --version
```

If you don't have Python installed, visit the official Python website (https://www.python.org) and download the latest version for your operating system. For Windows users, make sure to check the box that says "Add Python to PATH" during installation. Mac and Linux users can use package managers like Homebrew or apt to install Python. After installation, open a new terminal window and type "python --version" to verify that Python has been installed correctly. If you encounter any issues, consult the Python documentation for troubleshooting steps specific to your operating system.


### Step 2: Setup T4SG Virtual Environment 

While Python has a built-in environment that gives access to its standard library modules, we often need to use external packages as well. It's crucial to be cautious when installing packages for several reasons:

1. Different T4SG data science projects may require incompatible versions of the same package.
2. Modifying the system-wide Python installation could lead to unexpected issues if your OS relies on Python.
3. To ensure reproducibility, we need to keep track of the exact software versions used in our projects.

To address these concerns, we need a solution that allows us to create and manage separate Python environments, each with its own set of dependencies.

A [virtual environment](https://docs.python.org/3/library/venv.html#venv-def) is an isolated directory structure containing a specific Python version and a set of additional packages. This isolation allows for project-specific dependencies without affecting the system-wide Python installation.

Typically, Python distributions come with:
* [venv](https://docs.python.org/3/library/venv.html#module-venv) - a tool for creating and managing virtual environments
* [pip](https://docs.python.org/3/installing/index.html#installing-index) - a package installer for Python, used to download and manage third-party packages (primarily from PyPI)

Package managers like Conda and Micromamba extend the concept of a virtual environment to other languages. See the README for more details on packages managers & virtual environments. 

Within this folder, we have a `t4sg.yml` file that lists the packages we'll be using for this project --- we will provide a baseline set of packages, but this may be altered by your SSWE/PM depending on specific project functionality. It should be in the same directory as this notebook.

#### 1. Download Miniconda:

First, let's download Miniconda if you haven't already. 
   - Visit the [Miniconda website](https://docs.conda.io/en/latest/miniconda.html)
   - Choose the installer for your operating system (Windows, macOS, or Linux) (Note: for macOS users, select the 'pkg' installer, not the 'bash' installer.)
   - Follow the instructions on the installer to install Miniconda.

#### 2. Add Miniconda to your PATH:

Run `conda --version` in your terminal. If it still shows 'command not found', you'll need to add Miniconda to your PATH. To add Miniconda to your PATH, follow the instructions specific to your operating system:

- **Windows**:
  - Open the Start Menu and search for "Environment Variables".
  - Click on "Edit the system environment variables".
  - Click on the "Environment Variables" button.
  - In the "System variables" section, find the "Path" variable and click "Edit".
  - Click "New" and add the path to your Miniconda installation (e.g., `C:\Users\YourUsername\miniconda3\bin`).
  - Click "OK" to save the changes.

- **macOS and Linux**:
  - Open your terminal.
  - Add the following line to your `.bash_profile`, `.zshrc`, or `.profile` file:
    ```sh
    export PATH="/path/to/miniconda3/bin:$PATH"
    ```
  - Replace `/path/to/miniconda3/bin` with the actual path to your Miniconda installation.
  - Save the file and run `source ~/.bash_profile` (or the appropriate file) to apply the changes.

Now, try running `conda --version` in your terminal. If you see the version number, you've successfully added Miniconda to your PATH.

#### 3. Create the T4SG Environment

Next, to instruct miniconda to create a new environment from our T4SGyml specification, run the following in the terminal:
``` sh
conda env create -f t4sg.yml
```

Once all the packages have been installed, we can activate our new environment:
```sh
conda activate t4sg
```

You'll see your shell prompt now shows your active environment. You can use `deactivate` to turn it off. Remember to always activate your `t4sg` environment before working on your project.

### Step 3: Setup Kernel <a id="part3"></a>

This starter project will be in the form of a [Jupyter Notebook](https://jupyter.org/). They allow for the embedding of runnable code in a document of formatted text. It's recommend that you use Visual Studio Code (VSCode) as your development environment. To use Jupyter Notebooks with VSCode:

#### 1. Install the "Jupyter" extension 

- Open VSCode.
- Go to the Extensions view (Ctrl+Shift+X or Cmd+Shift+X on macOS).
- Search for "Jupyter".
- Install the official Jupyter extension by Microsoft.
      
After installing the Jupyter extension on VSCode, you should now be able to open or create a Jupyter Notebook by creating an .ipynb file in VSCode.

#### 2. Adding Virtual Environment as a Kernel

Next, to be able to run your notebook, you must make sure to add the T4SG virtual environment as a kernel. Here's how you can find and add your virtual environment to VSCode:
- First, activate your virtual environment in the terminal:
```sh
micromamba activate t4sg
```
- With the environment activated, run this command to get the path to your Python interpreter:
```sh
which python
```
This will output a path like /path/to/your/micromamba/envs/t4sg/bin/python.
- In VSCode, open the Command Palette (Cmd+Shift+P on macOS or Ctrl+Shift+P on Windows/Linux). Type "Python: Select Interpreter" and choose this option. Click on "Enter interpreter path..." at the bottom of the list. Paste the path you got from step 2 into the input box. VSCode should now recognize this as a valid interpreter and add it to your list of available kernels.
- Open your Jupyter notebook again and try selecting the kernel. You should now see your 't4sg' environment listed. If you still don't see the environment, you may need to restart VSCode for the changes to take effect.

After selecting the t4sg kernel, you should now be able to run a code cell, and have access to all the packages listed in the t4sg.yml file.

#### 3. Selecting the Correct Kernel

Next, to run your notebook, you must make sure to select the correct kernel. To ensure you're using the correct Python environment (kernel) for your Jupyter Notebook in VSCode:

- Open your Jupyter Notebook in VSCode.
- Look for the "Select Kernel" button in the top-right corner of the notebook.
- Click on it and choose the kernel that corresponds to your 't4sg' environment. You may need to choose the 'Select Another Kernel...' option and then go to 'Python Environments...', where you should see the 't4sg' environment listed.
4. If you don't see your 't4sg' environment, you may need to restart VSCode or manually add the kernel path (see above).

Remember to activate your 't4sg' environment before launching VSCode to ensure it's available as a kernel option.

 
#### 4. Running Cells

To run a Jupyter Notebook cell in VSCode:
- Click inside the cell you want to run
- Use the keyboard shortcut:
   - Mac: Shift (or Ctrl) + Enter
   - Windows: Shift + Enter
Alternatively, you can:
- Click the "Run Cell" play button that appears to the left of the cell
- Use the "Run" button in the top menu of the notebook

When you run a cell, VSCode sends the code to the Jupyter kernel (in this case, the 't4sg' environment we set up). The kernel executes the code and sends the results back to VSCode, which then displays the output below the cell. For code cells, the output will be the result of the last expression or any print statements. For markdown cells, the rendered markdown will be displayed.

 You can run cells in any order, and variables/functions defined in one cell are available in subsequent cells. This allows for an interactive and iterative coding experience. Try running the cell below to install some key packages that you may use. The primary libraries we will be using are:
- numpy: Provides a fast numerical array structure and helper functions.
- pandas: Provides a DataFrame structure to store data in memory and work with it easily and efficiently.
- scikit-learn: The essential Machine Learning package in Python.
- matplotlib: Basic plotting library in Python; most other Python plotting libraries are built on top of it.
- seaborn: Advanced statistical plotting library.

## More information and resources

### More about virtual environments and package managers

Virtual environments are isolated Python environments that allow you to manage project-specific dependencies without interfering with system-wide Python installations or other projects. They are essential for several reasons:

1. **Dependency Isolation**: Each project can have its own set of dependencies, avoiding conflicts between different versions of packages required by different projects.

2. **Reproducibility**: Virtual environments make it easier to recreate the exact environment in which a project was developed, ensuring consistency across different machines or for different developers.

3. **Clean Testing**: They provide a clean, isolated environment for testing code without the influence of globally installed packages.

4. **Version Control**: Virtual environments can be easily recreated from a requirements file, making it simple to version control your project's dependencies.

5. **System Protection**: They prevent accidental modifications to your system-wide Python installation, maintaining the stability of your operating system.

Package managers are tools that complement and extend the functionality of virtual environments. While virtual environments provide isolated spaces for Python projects, package managers handle the installation, upgrading, and management of software packages within these environments. Here's how package managers enhance the virtual environment ecosystem:

1. **Dependency Resolution**: Package managers like pip (Python's default package installer) can automatically resolve and install dependencies required by a package, ensuring all necessary components are present in your virtual environment.

2. **Version Control**: They allow you to specify exact versions of packages, ensuring consistency across different installations of your project.

3. **Easy Installation and Removal**: Package managers simplify the process of adding or removing packages from your virtual environment with simple commands.

4. **Requirements Files**: They can generate and read requirements files, which list all packages and their versions used in a project. This makes it easy to recreate the exact environment on another machine.

5. **Package Discovery**: Many package managers provide ways to search for and discover new packages that might be useful for your project.

6. **Environment Reproduction**: In conjunction with virtual environments, package managers enable you to easily reproduce your development environment on different machines or for different team members.

7. **Conflict Prevention**: By managing packages within a specific virtual environment, package managers help prevent conflicts between different versions of packages that might be required by different projects.

8. **Update Management**: They provide mechanisms to update packages to their latest versions, either individually or all at once, while respecting version constraints.

Popular package managers in the Python ecosystem include:

- **pip**: The default package installer for Python, used in conjunction with virtual environments created by venv or virtualenv.
- **conda**: Part of the Anaconda distribution, conda can manage packages and environments for multiple programming languages, not just Python.

By leveraging both virtual environments and package managers, you can create reproducible, isolated, and well-managed development environments for your Python projects.

Two popular package managers in the Python ecosystem are Conda and Micromamba:

#### Mamba & Micromamba

Mamba and Micromamba are powerful package management tools for Python and other programming languages. Here's a brief introduction to both:

Mamba:
Mamba is a fast, robust, and cross-platform package manager. It's a reimplementation of the conda package manager in C++, which makes it significantly faster than conda, especially in solving complex dependency trees. Mamba uses the same package format and repository structure as conda, making it fully compatible with existing conda packages and environments.

Micromamba:
Micromamba is a tiny version of the mamba package manager. It's a single, self-contained executable that can be used to bootstrap conda-compatible environments on Linux, macOS, or Windows. Micromamba doesn't require an existing Python installation and can even install the desired version of Python for your environment. It's particularly useful for CI/CD pipelines, containers, or situations where a minimal footprint is desired.

To get started with Micromamba, consult the [official documentation](https://mamba.readthedocs.io/en/latest/installation.html#micromamba) for up-to-date installation instructions for your operating system. Once installed, Micromamba will typically modify your shell's configuration to ensure that both the `micromamba` executable and the directory for storing virtual environments are added to your PATH.

#### Conda & Miniconda

[**Conda**](https://conda.io/en/latest/index.html) is a powerful package management system and environment management system that runs on Windows, macOS, and Linux. Conda quickly installs, runs, and updates packages and their dependencies. It also easily creates, saves, loads, and switches between environments on your local computer.

While conda is generally slower than Mamba due to its Python implementation, it has some advantages:
1. Maturity and stability: Conda has been around longer and is more extensively tested.
2. Wider adoption: More users and more community resources available.
3. Direct integration with Anaconda: If you're using the full Anaconda distribution, conda is natively integrated.

[Miniconda](https://docs.conda.io/en/latest/miniconda.html) is a free minimal installer for conda. It's a small, bootstrap version of Anaconda that includes only conda, Python, the packages they depend on, and a small number of other useful packages. If you need a minimal conda installation and don't require the additional packages that come with the full Anaconda distribution, Miniconda is an excellent choice.

Given these advantages, _we suggest opting for a **conda** variant instead of mamba. However, the package manager specifics of your project are up to the SSWE & PM of your project.


For a more comprehensive understanding of virtual environments and package managers, refer to the Python documentation on [virtual environments & packages](https://docs.python.org/3/tutorial/venv.html?highlight=pip).


### More about Pandas

Pandas is a powerful data manipulation and analysis library for Python. It provides data structures like DataFrames and Series that allow for efficient handling of structured data, along with a wide range of functions for data cleaning, transformation, and analysis. Pandas is particularly well-suited for working with tabular data, time series, and heterogeneous data types.

For more information on Pandas, you can refer to the following resources:

- [Pandas User Guide](https://pandas.pydata.org/docs/user_guide/index.html): Comprehensive documentation covering all aspects of Pandas.
- [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html): A quick introduction to the main concepts and features of Pandas.
- [Pandas Cookbook](https://pandas.pydata.org/docs/user_guide/cookbook.html): A collection of practical recipes for solving various data manipulation tasks.

### More about Matplotlib

Matplotlib is a comprehensive library for creating static, animated, and interactive visualizations in Python. It provides a MATLAB-like interface for creating plots and graphs. Matplotlib is highly customizable and can produce publication-quality figures in various formats.

For more information, you can refer to the following Matplotlib documentation:

- [Matplotlib User's Guide](https://matplotlib.org/stable/users/index.html): A comprehensive guide to using Matplotlib.
- [Matplotlib Tutorials](https://matplotlib.org/stable/tutorials/index.html): Step-by-step tutorials for various plotting techniques.
- [Matplotlib Examples](https://matplotlib.org/stable/gallery/index.html): A gallery of example plots with source code.

Matplotlib serves as the foundation for many other visualization libraries in Python, including Seaborn, which we'll discuss next.

### More about Seaborn

Seaborn is a statistical data visualization library built on top of Matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics. Seaborn is particularly useful for creating complex visualizations with just a few lines of code, and it integrates well with Pandas DataFrames.

Key features of Seaborn include:

- Built-in themes for styling Matplotlib graphics
- Tools for choosing color palettes to make beautiful plots that reveal patterns in your data
- Functions for visualizing univariate, bivariate, and multivariate distributions
- Tools for visualizing statistical relationships between variables

For more information, you can refer to the following Seaborn documentation:

- [Seaborn Tutorial](https://seaborn.pydata.org/tutorial.html): A comprehensive guide to using Seaborn.
- [Seaborn Example Gallery](https://seaborn.pydata.org/examples/index.html): A collection of example plots with source code.
- [Seaborn API Reference](https://seaborn.pydata.org/api.html): Detailed documentation of Seaborn's functions and classes.
