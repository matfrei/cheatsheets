# Package management with uv

## Create new environment and pyproject.toml
``` uv init ```

## Add package to .venv
``` uv add <packagename> ```

## Make sure all dependencies in pyproject.toml are installed
``` uv sync ```

## Migrate from a requirements.txt file
```  uv add -r requirements.txt ```

## Run commands
``` uv run file.py```
