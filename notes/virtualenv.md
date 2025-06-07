---
tags: [python]
title: virtualenv
created: '2019-07-30T06:19:49.221Z'
modified: '2025-06-07T08:54:59.061Z'
---

# virtualenv

> tool to create isolated python environments

[[python]], [[pyenv]]

## install

```sh
pip install virtualenv --verbose
pip3 install virtualenv
```

[[pip]]

## usage

```sh
virtualenv VIRTUALENV_NAME

source VIRTUALENV_NAME/bin/activate     # activate virtualenv in project
pip install pre-commit                  # install to virtualenv


pip3 install virtualenv
virtualenv venv --python=python3.8
source venv/bin/activate
```

```sh
python3 -m venv ./venv
source ./venv/bin/activate      # activate virtual env
type python pip python3 pip3    # show different paths
```

## see also

- [[sam]]
- [[12 factor app]]
- [Stack Overflow - Virtualenv Command Not Found](https://stackoverflow.com/a/36577160)
- [virtualenv.pypa.io/en/latest/](https://virtualenv.pypa.io/en/latest/)
