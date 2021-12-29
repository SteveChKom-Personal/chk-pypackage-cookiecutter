# Makefile
SHELL := /bin/bash

.PHONY: init
init:
	# For the very first time a project is being develop
	# Initialise virtual environment to ensure code formatting and testing checks are available
	pipenv install build --dev
	pipenv install black --dev
	pipenv install isort --dev
	pipenv install flake8 --dev
	pipenv install mypy --dev
	pipenv install pytest --dev
	pipenv install pytest-cov --dev
	pipenv install pre-commit --dev
	pipenv install interrogate --dev
	pipenv install coverage --dev
	pipenv install tox --dev
	pipenv install sqlalchemy
	pipenv install pymysql
	pipenv install pandas
	pipenv install numpy

.PHONY: build
build:
	# Create package for use elsewhere
	pipenv run python -m build

.PHONY: enable-precommit
enable-precommit:
	pipenv run pre-commit install

.PHONY: disable-precommit
disable-precommit:
	pipenv run pre-commit uninstall

.PHONY: install-editable
install-editable:
	pipenv install -e .

.PHONY: run
run:
	pipenv run {{ cookiecutter.package_name }}

.PHONY: jupyter-kernel
jupyter-kernel:
	# Set up jupyterlab kernel for this project
	pipenv install ipykernel --dev
	sudo python -m ipykernel install --user --name=$(notdir $(shell pwd))
	jupyter kernelspec list

.PHONY: jupyter-kernel-uninstall
jupyter-kernel-uninstall:
	# Remove jupyter kernel specific for this project
	sudo jupyter kernelspec uninstall $(notdir $(shell pwd))

.PHONY: pytest
pytest:
	# Execute the tests against the local copy directly
	# see https://doc.pytest.org/en/latest/explanation/goodpractices.html for different behaviour when e.g. running tox
	python -m pytest
	coverage run --module pytest
	coverage report -m
