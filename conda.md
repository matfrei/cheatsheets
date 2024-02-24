# useful commands for anaconda environments

## create an anaconda environment

```
conda create --name envname python=3.10
```

## create an anaconda environment in a specificed directory

```
conda env create --prefix /path/to/dir
```
## export an anaconda enviroment to a .yaml file
```
conda env export environment-name.yml
```


## downgrade python install in a conda environment
```
conda install python=3.7
```

## add conda kernel to jupyter
```
python -m ipykernel install --user --name=firstEnv
```

## find all python versions on a machine
```
whereis python3
```
## init conda base env when you haven't configured your bashrc file to do so by default
```
eval "$(/PATH/TO/ANACONDA/bin/conda shell.bash hook)" 
```
or for any other shell
```
eval "$(/PATH/TO/ANACONDA/bin/conda shell.YOUR_SHELL_NAME hook)" 
```

