# Setting Up Python

> Installing Python via the Anaconda distribution and configuring Visual Studio Code to run Python scripts and Jupyter notebooks.

Two primary sources for installation of Python packages are the [Python's official distribution](https://www.python.org) and the [Anaconda distribution](https://www.anaconda.com/). Each of them use their own package installers (pip and conda respectively) to install and update packages as well as create virtual environments to support multiple versions of Python in the same machine.

Owing to some advantages (package dependency analysis and math kernel optimization libraries) of the Anaconda distribution the over the official Python one, by default, we will be using the Anaconda distribution unless specifically mentioned otherwise.

## Installing the Anaconda Individual Edition
![Conda](https://img.shields.io/conda/vn/conda-forge/conda?label=version&style=flat-square)
![Conda](https://img.shields.io/conda/dn/conda-forge/conda?style=flat-square)

Originally aimed for data science and machine learning, the *Anaconda Individual Edition* is a free distribution for Python and R programming languages constituting of a large number of packages for both. The package manager *conda* analyzes the installed packages and verifies the dependencies making the installation breakdown-proof for existing projects. A light-weight, minimal edition of the distribution is also available under the name [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

### On Windows/MacOS

Download the graphical installer (```.exe```/```.pkg```) for the latest version of Anaconda Python from the [individual product download page](https://www.anaconda.com/products/individual) for the specific version of your operating system and run the installer.

***Note: If Anaconda is the only distribution of Python in your system, make sure to check both "Add Anaconda to the system PATH environment variable" and "Register Anaconda as the system Python 3.x".***

### On Linux

Download the generic command line installer (```.sh```) for the latest version of Anaconda Python from the [individual product download page](https://www.anaconda.com/products/individual) and install it by running the following command in the terminal, replacing ```path/to/file``` with the complete path to the directory of the downloaded installer along with the file name:

```bash
bash path/to/file.sh
```

***Note: Linux usually comes with official Python distributions accessible through ```python3``` for version 3.x and ```python``` for version 2.x.***

## Initializing the conda Environment

*conda-forge* is a community-driven packaging system for conda dedicated for the scientific computing community. It provides a wide collection of recipies, build infrastructure and distributions. To add it as the first-hit channel, open the Anaconda command prompt in the elevated (administrator) mode and execute the following lines:

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

Initialize the conda environment using:

```bash
conda init
```

To verify the version of Python installed, run:

```bash
python --version
```

The output should be of the form:

```bash
Python 3.x.x
```

## [Optional] Managing Anaconda Packages

To install a package, use the following command by replacing ```package``` with its name and ```version``` with its requied version:

```bash
conda install package=version
```

To install multiple packages, append them one after the other separated by spaces.

To list all installed packages, use:

```bash
conda list
```

To update all packages, use:

```bash
conda update --all
```

To remove a package, use the following command by replacing ```package``` with its name:

```bash
conda remove package
```

## [Optional] Installing Visual Studio Code

[![GitHub package.json version](https://img.shields.io/github/package-json/v/Microsoft/vscode?style=flat-square)](https://github.com/microsoft/vscode)

*Visual Studio Code* (VSCode) is an open-source, highly-customizable and versatile source-code editor developed by Microsoft which supports debugging, version control, syntax highlighting, intelligent code completion, snippets, and code refactoring. Download the appropriate setup file for your operating system (Windows/Linux/MacOSX) from the [official page](https://code.visualstudio.com/download) and install. Easy!

## [Optional] Installing Microsoft's Python Extension of VSCode

[![GitHub package.json version](https://img.shields.io/visual-studio-marketplace/v/ms-python.python?style=flat-square)](https://github.com/microsoft/vscode)
[![GitHub package.json version](https://img.shields.io/visual-studio-marketplace/i/ms-python.python?style=flat-square)](https://github.com/microsoft/vscode)

*Python* extension for VSCode by Microsoft provides a rich support for the language including a whole bundle of features for easy execution of Python scripts. Install the latest version of this extension from VSCode's Marketplace, the last icon on VSCode's *activity bar* (left edge). It usaully stays at the top with over 20M installations.