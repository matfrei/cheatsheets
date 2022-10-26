# Cheatsheet for managing virtual environments using pythons virtualenv package

## Create a new virtual environment using virtualenv
```
cd env_basepath
virtualenv --system-site-packages -p python3 env_name
```
## Load a virtualenv environement
```
source env_basepath/env_name/bin/activate
```
## Install packages using pip into a specific virtual environment

```
pip install packagename --target env_basepath/env_name/
```

## Wrap virtuelenv environment into jupyter kernel
```
python -m ipykernel install --user --target env_basepath/env_name/

```
## Install code from github repository to environment
```
pip install git+https://path.to.repo.git --target env_basebatch/env_name/
```

### Install code from a subfolder or subpackage on github
Example: pycocotools
```
pip install -U 'git+https://github.com/leimao/cocoapi.git#subdirectory=PythonAPI'

