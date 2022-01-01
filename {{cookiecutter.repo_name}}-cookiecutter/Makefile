# Makefile
SHELL := /bin/bash

.PHONY: init
init: ## First time initialisation of virtual environment to ensure code formatting and testing checks are available
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
	pipenv install twine --dev
	pipenv install tox --dev
	pipenv install sqlalchemy
	pipenv install pymysql
	pipenv install pandas
	pipenv install numpy
	pipenv install types-pyyaml

.PHONY: build
build: ## Create package for use elsewhere
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

.PHONY: clean-build
clean-build: ## remove build artifacts
	rm -fr build/
	rm -fr dist/
	rm -fr .eggs/
	find . -name '*.egg-info' -exec rm -fr {} +
	find . -name '*.egg' -exec rm -f {} +

.PHONY: clean
clean: clean-pyc clean-test ## remove test, coverage and Python artifacts

.PHONY: clean-pyc
clean-pyc: ## remove Python file artifacts
	find . -name '*.pyc' -exec rm -f {} +
	find . -name '*.pyo' -exec rm -f {} +
	find . -name '*~' -exec rm -f {} +
	find . -name '__pycache__' -exec rm -fr {} +

.PHONY: clean-test
clean-test: ## remove test and coverage artifacts
	rm -fr .tox/
	rm -f .coverage
	rm -fr htmlcov/
	rm -fr .pytest_cache

.PHONY: run
run:
	pipenv run {{ cookiecutter.package_name }}

.PHONY: jupyter-kernel
jupyter-kernel: ## Set up jupyterlab kernel for this project
	pipenv install ipykernel --dev
	sudo python -m ipykernel install --user --name=$(notdir $(shell pwd))
	jupyter kernelspec list

.PHONY: jupyter-kernel-uninstall
jupyter-kernel-uninstall: ## Remove jupyter kernel specific for this project
	sudo jupyter kernelspec uninstall $(notdir $(shell pwd))

.PHONY: pytest
pytest:
	## Execute the tests against the local copy directly
	## see https://doc.pytest.org/en/latest/explanation/goodpractices.html for different behaviour when e.g. running tox
	python -m pytest
	coverage run --module pytest
	coverage report -m

.PHONY: tox
test-all:
	tox