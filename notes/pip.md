---
tags: [python]
title: pip
created: '2019-08-02T07:21:18.995Z'
modified: '2025-06-07T08:56:10.256Z'
---

# pip

> package-management system used to install and manage software packages written in python

[[pip3]], [[python]]

## install

```sh
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py 
python get-pip.py --force-reinstall
```

[[curl]]

## usage

```sh
pip list

pip install virtualenv --verbose    # --verbose see where package gets installed to

pip install PACKAGE --user          # avoid "Operation not permitted" and using sudo
```

## see also

- [[virtualenv]]
- [[gem]]
- [[curl]]
- [How do I install pip on macOS or OS X? - Stack Overflow](https://stackoverflow.com/questions/17271319/how-do-i-install-pip-on-macos-or-os-x)
- [How to install and use pip without sudo - GitHub](https://gist.github.com/haircut/14705555d58432a5f01f9188006a04ed)
