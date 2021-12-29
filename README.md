# chk-pypackage-cookiecutter

Python package template, providing
- a standard folder structure
- a test suites

## Setting up the repository
- Create/clone (empty) repository (from git) where the package resides
- Clone cookiecutter project
```
cookiecutter https://github.com/SteveChKom-Personal/chk-pypackage-cookiecutter.git
```
- Follow the prompts to fill in details
- Depending on how the repository and environment is set up, may need to move the generated files to the 'right place' with the following filestructure
```
repo-folder
|- src
    |- cookiecutter.package_name
        |- __init__.py
           ...
       ...
|- tests
|- Pipfile
|- pyproject.toml
|- ...
```

## Initialisation
- Use the Makefile from the cookiecutter output and ```make init``` to populate Pipfile

### NOW READY TO DEVELOP!