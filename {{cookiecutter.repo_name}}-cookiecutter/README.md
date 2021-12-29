# {{ cookiecutter.repo_name}}
{{ cookiecutter.description }}

## Initialisation
```
make init
```
Useful for the very first time this package is being developed, this command will install packages useful for coding standards and tests.

## Installation
```
make install-editable
```
This command will install the package `{{ cookiecutter.package_name }}` in editable model (requires pipenv).

## Package
```
make build
```
This command will build a python package saved in dist that can be installed by other projects.

## Run
```
make run
```
This command will run the package `{{ cookiecutter.package_name }}`

## jupyter-kernel
```
make jupyter-kernel
```
This command will install jupyter kernel outside pipenv to enable code development using jupyter

## jupyter-kernel-uninstall
```
make jupyter-kernel-uninstall
```
This command will uninstall the jupyter kernel for this project


