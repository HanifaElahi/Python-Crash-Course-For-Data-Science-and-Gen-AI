# Agenda

- Installations [Extensions]
- Environments [Importance of Environments]
- Python Packages [Using setup.py file, pyproject.toml]
- .env File [Keys, Configurations]

## Importance of Environments

When working in a company as an architect, you may be involved in multiple projects simultaneously, each with different requirements. Managing dependencies and versions across these projects can be challenging without proper environment isolation.

### Example Scenarios:

#### Project 1: ML Ops Tools & EDA

- Required Python Version: 3.7
- Dependencies: Libraries related to ML Ops, EDA, etc.

#### Project 2: NLP

- Required Python Version: 3.10
- Dependencies: Transformers and other related libraries

#### Project 3: Agentic AI

- Required Python Version: 3.12
- Dependencies: LangChain, LangGraph, etc.

### Why Separate Environments Matter:

Installing all these packages in a single environment can lead to version conflicts and compatibility issues. For instance, a library needed for Project 1 might not work well with the Python version or dependencies required for Project 3.

### Solution:

Create separate environments for each project to ensure compatibility and smooth development:

- Project 1 Environment (Python 3.7)
- Project 2 Environment (Python 3.10)
- Project 3 Environment (Python 3.12)

This approach prevents version conflicts and allows you to work on each project independently.

## Setting Up Environments

1. **Using Virtual Environments (venv):**

   ```bash
   python3.12 -m venv venv
   source venv/bin/activate
   ```
venv
2. **Using Conda:**

   - Create an environment with a specific name:

     ```bash
     conda create -n project1_env python=3.7
     conda activate project1_env
     ```

   - Create an environment in the current working directory:

     ```bash
     conda create -p venv python==3.12
     ```

     This will create the environment in the current working directory. The `-p` flag specifies the present working directory.

     ```bash
     conda create -n venv python==3.12
     ```

    This command creates a new environment named "venv" with Python version 3.12. By default, the environment and its packages will be installed in the directory where Anaconda is set up.

## Python Packages

### Installing Python Packages

There are multiple ways to install packages in Python:

#### 1. Using `pip install`
You can install packages individually with the following command:

```bash
pip install package_name
```

#### 2. Using `requirements.txt` (Industry Standard)
This is the preferred approach in professional environments, as it allows developers to see all the required packages and their versions in one place. You can install packages from a `requirements.txt` file with:

```bash
pip install -r requirements.txt
```

`-r` is more like read mode.
This ensures consistency across different development environments.

### Python Project Packaging

#### 1. setup.py

A `setup.py` file is used to define how a Python project is packaged and distributed. It includes metadata like the package name, version, author, and dependencies.

`__init__.py`

The __init__.py file makes a directory (e.g., src/) a Python package. It can be an empty file or contain package initialization code.

`-e . in requirements.txt`

The -e . line in a requirements.txt file is used to trigger and execute the setup.py file in the current directory.


#### 2. pyproject.toml

`pyproject.toml` is a modern standard for packaging Python projects. It specifies the build system requirements and project dependencies in a more readable and standardized format. Much more efficient than setup.py

- need setuptools and wheel.
