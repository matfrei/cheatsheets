# Package management with uv

## Create new environment and pyproject.toml
``` uv init ```

## Add a dependency
``` uv add <packagename> ```

## Remove a dependency
``` uv remove <packagename> ```

## Upgrade a dependency
``` uv lock --upgrade-package <package_name> ```

## Lock dependencies (fix all the versions of your dependencies and sub-dependencies)
``` uv lock ```
**TODO: clarify: in which cases would that need to happen manually, and what is the difference to pyproject.toml)**

## Make sure all dependencies in pyproject.toml are installed
``` uv sync ```

## Migrate from a requirements.txt file
```  uv add -r requirements.txt ```

## Run commands
``` uv run file.py ```
