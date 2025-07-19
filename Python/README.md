# Python Commands Reference

## Installation & Version Management

```bash
# Check Python version
python --version
python3 --version

# Install Python (Linux)
sudo apt-get install python3

# Install Python (macOS with Homebrew)
brew install python

# Install Python (Windows)
# Download installer from python.org

# Install pyenv (Python version manager)
## Linux/macOS
curl https://pyenv.run | bash
## Windows
# Use pyenv-win from GitHub

# List available Python versions with pyenv
pyenv install --list

# Install specific Python version with pyenv
pyenv install 3.10.0

# Set global Python version with pyenv
pyenv global 3.10.0

# Set local Python version with pyenv
pyenv local 3.10.0
```

## Virtual Environments

```bash
# Create virtual environment (venv)
python -m venv myenv
python3 -m venv myenv

# Activate virtual environment
## Windows
myenv\Scripts\activate
## Linux/macOS
source myenv/bin/activate

# Deactivate virtual environment
deactivate

# Create virtual environment with conda
conda create --name myenv python=3.10

# Activate conda environment
conda activate myenv

# Deactivate conda environment
conda deactivate

# List conda environments
conda env list

# Remove conda environment
conda env remove --name myenv

# Create virtual environment with virtualenvwrapper
mkvirtualenv myenv

# Activate virtualenvwrapper environment
workon myenv

# Deactivate virtualenvwrapper environment
deactivate

# Remove virtualenvwrapper environment
rmvirtualenv myenv
```

## Package Management

```bash
# Install a package
pip install package-name

# Install a specific version
pip install package-name==1.2.3

# Install from requirements file
pip install -r requirements.txt

# Upgrade a package
pip install --upgrade package-name

# Uninstall a package
pip uninstall package-name

# List installed packages
pip list

# Show package information
pip show package-name

# Search for packages
pip search package-name

# Generate requirements file
pip freeze > requirements.txt

# Install development packages
pip install -e .

# Install packages in user space
pip install --user package-name

# Clear pip cache
pip cache purge
```

## Running Python

```bash
# Run Python interactively
python
python3

# Run a Python script
python script.py
python3 script.py

# Run a Python module
python -m module_name

# Run with environment variables
ENV_VAR=value python script.py

# Run with optimizations
python -O script.py

# Run with verbose import messages
python -v script.py

# Run with warnings
python -W all script.py

# Run with site packages disabled
python -S script.py

# Run with unbuffered stdout/stderr
python -u script.py

# Run with Python debugger
python -m pdb script.py
```

## Interactive Python

```bash
# Start IPython
ipython

# Start Jupyter Notebook
jupyter notebook

# Start Jupyter Lab
jupyter lab

# Start Python with auto-completion
python -m readline

# Start IDLE (Python's IDE)
idle
idle3

# Start Python with pretty printing
python -m pprint
```

## Code Quality & Linting

```bash
# Run pylint
pylint script.py

# Run flake8
flake8 script.py

# Run black code formatter
black script.py

# Run isort import sorter
isort script.py

# Run mypy type checker
mypy script.py

# Run bandit security linter
bandit -r project_directory

# Run autopep8 code formatter
autopep8 --in-place script.py

# Run yapf code formatter
yapf --in-place script.py
```

## Testing

```bash
# Run unittest discovery
python -m unittest discover

# Run pytest
pytest

# Run pytest with verbose output
pytest -v

# Run specific test file
pytest test_file.py

# Run specific test function
pytest test_file.py::test_function

# Run tests matching pattern
pytest -k "pattern"

# Run tests with coverage
pytest --cov=package_name

# Generate coverage report
pytest --cov=package_name --cov-report=html

# Run doctests
python -m doctest script.py

# Run tox for multi-environment testing
tox
```

## Documentation

```bash
# Generate Sphinx documentation
sphinx-quickstart
sphinx-build -b html source_dir build_dir

# Generate pydoc documentation
python -m pydoc -w module_name

# Start pydoc server
python -m pydoc -p 8000

# Generate pdoc documentation
pdoc --html module_name
```

## Packaging & Distribution

```bash
# Create a source distribution
python setup.py sdist

# Create a wheel distribution
python setup.py bdist_wheel

# Build with setuptools
pip install build
python -m build

# Upload to PyPI
twine upload dist/*

# Check distribution
twine check dist/*

# Install from local source
pip install -e .

# Create a Python package with cookiecutter
cookiecutter https://github.com/audreyfeldroy/cookiecutter-pypackage.git
```

## Profiling & Debugging

```bash
# Profile with cProfile
python -m cProfile script.py

# Profile with cProfile and sort by time
python -m cProfile -s time script.py

# Profile with cProfile and save to file
python -m cProfile -o profile.prof script.py

# View profile with pstats
python -m pstats profile.prof

# Profile with line_profiler
kernprof -l script.py
python -m line_profiler script.py.lprof

# Memory profiling
mprof run script.py
mprof plot

# Debug with pdb
python -m pdb script.py

# Debug with ipdb
python -m ipdb script.py
```

## Web Development

```bash
# Install Django
pip install django

# Create Django project
django-admin startproject project_name

# Create Django app
python manage.py startapp app_name

# Run Django development server
python manage.py runserver

# Run Django migrations
python manage.py migrate

# Create Django migrations
python manage.py makemigrations

# Install Flask
pip install flask

# Run Flask development server
flask run

# Run Flask with debug mode
flask --debug run

# Install FastAPI
pip install fastapi uvicorn

# Run FastAPI server
uvicorn main:app --reload
```

## Data Science

```bash
# Install data science packages
pip install numpy pandas matplotlib seaborn scikit-learn

# Install TensorFlow
pip install tensorflow

# Install PyTorch
pip install torch torchvision
```

## Jupyter

```bash
# Install Jupyter
pip install jupyter

# Install JupyterLab
pip install jupyterlab

# Start Jupyter Notebook
jupyter notebook

# Start Jupyter Lab
jupyter lab

# Start Jupyter Notebook with specific port
jupyter notebook --port=8888

# Start Jupyter Notebook without opening browser
jupyter notebook --no-browser

# Start Jupyter Notebook with a specific directory
jupyter notebook --notebook-dir=/path/to/directory

# Start Jupyter Notebook with a specific config file
jupyter notebook --config=/path/to/config.py

# List running Jupyter servers
jupyter notebook list

# Stop a specific Jupyter server
jupyter notebook stop 8888

# Generate Jupyter config file
jupyter notebook --generate-config

# Set password for Jupyter
jupyter notebook password

# Install Jupyter extensions
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user

# Enable specific extension
jupyter nbextension enable extension_name/main

# Install Jupyter themes
pip install jupyterthemes

# List available themes
jt -l

# Apply a theme
jt -t theme_name

# Reset to default theme
jt -r

# Convert Jupyter notebook to other formats
jupyter nbconvert --to html notebook.ipynb
jupyter nbconvert --to pdf notebook.ipynb
jupyter nbconvert --to script notebook.ipynb  # Convert to Python script
jupyter nbconvert --to markdown notebook.ipynb
jupyter nbconvert --to slides notebook.ipynb  # Create presentation

# Run notebook from command line
jupyter nbconvert --to notebook --execute notebook.ipynb

# Run notebook and save output to new file
jupyter nbconvert --to notebook --execute notebook.ipynb --output executed_notebook

# Start notebook with specific kernel
jupyter notebook --kernel=python3

# List available kernels
jupyter kernelspec list

# Install a new kernel
python -m ipykernel install --name env_name --display-name "Python (env_name)"

# Remove a kernel
jupyter kernelspec uninstall env_name

# Start JupyterLab with specific settings
jupyter lab --collaborative  # Enable real-time collaboration

# Install JupyterLab extensions
jupyter labextension install @jupyterlab/extension-name

# List installed JupyterLab extensions
jupyter labextension list

# Update JupyterLab extensions
jupyter labextension update --all

# Build JupyterLab (after extension changes)
jupyter lab build

# Start Jupyter in a specific virtual environment
source myenv/bin/activate && jupyter notebook  # Linux/macOS
myenv\Scripts\activate && jupyter notebook  # Windows
```

## Environment & Configuration

```bash
# List Python path
python -c "import sys; print(sys.path)"

# Check Python installation location
which python
where python  # Windows

# Check Python executable path
python -c "import sys; print(sys.executable)"

# Check loaded modules
python -c "help('modules')"

# Install python-dotenv
pip install python-dotenv

# Load environment variables from .env file
python -m dotenv run script.py
```

## Miscellaneous

```bash
# Create a new Python file
touch script.py  # Linux/macOS
echo. > script.py  # Windows

# Make a Python script executable (Linux/macOS)
chmod +x script.py

# Run HTTP server
python -m http.server 8000

# Run SMTP debugging server
python -m smtpd -n -c DebuggingServer localhost:1025

# Pretty-print JSON
python -m json.tool file.json

# Encode/decode base64
python -c "import base64; print(base64.b64encode(b'hello').decode())"
python -c "import base64; print(base64.b64decode(b'aGVsbG8=').decode())"

# Generate a UUID
python -c "import uuid; print(uuid.uuid4())"

# Get current timestamp
python -c "import time; print(time.time())"

# Format current date/time
python -c "import datetime; print(datetime.datetime.now().strftime('%Y-%m-%d %H:%M:%S'))"
```