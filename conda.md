# useful commands for anaconda environments

## create an anaconda environment

```
conda env create --name envname
```

## create an anaconda environment in a specificed directory

```
conda env create --prefix /path/to/dir
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

