# Cheatsheet for pythons virtualenv package

## Create a new virtual environment using virtualenv
'''
cd env_basepath
virtualenv --system-site-packages -p python3 env_name
'''
## Load a virtualenv environement
'''
source env_basepath/env_name/bin/activate
'''
## Install packages using pip into a specific virtual environment
'''
pip install packagename --target=env_basepath/env_name/
'''




