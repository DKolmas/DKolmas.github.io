---
title: "Python Virtual Environment"
date: 2020-12-26
categories: [Snippet]
tags: [Python]
excerpt: "A set of commands used to create Python VM"
mathjax: "true"
classes: wide
---

Check version of already installed pip version (globally)
 - python3 -m pip --version

Upgrade pip to the newest version
* python3 -m pip install -U pip

Create Python virtual environment
* python3 -m venv /path/to/new/virtual/environment

List all already created virtual environments
* Go to directory location where you install your all venvs (assuming you know the one)

Activate virstual envornment
* source theEnvornment/bin/activate

Check version of pip in theEnvironment
* python -m pip --version

Upgrade pip versoin in theEnvrionment
* python -m pip install -U pip

List all installed already packages
* python -m pip list

Update setuptools package
* python -m pip install --upgrade setuptools

Install missing packages (scipy will be installed automatically)
* python -m pip install numpy pandas jupyterlab matplolib seaborn scikit-learn

List installed packages
* python -m pip list

Deactivate theEnvironment
* deactivate
