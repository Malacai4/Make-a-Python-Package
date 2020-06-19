# Make-a-Python-Package
This repository will teach you how to make python packages, and upload them to 'pypi.org'!

## Directory Structure
hello/
  setup.py
  README.md
  LICENSE
  MANIFEST.in
  hello/
    ```__init__.py```
    hello.py
    
## 1. setup.py
```python
from setuptools import setup

def readme():
    with open('README.md') as f:
        README = f.read()
    return README

setup(
    name="hello",
    version="1.0.0",
    description="A Python package that says hello.",
    long_description=readme(),
    long_description_content_type="text/markdown",
    url="https://github.com/Malacai4/hello",
    author="Malacai Hiebert",
    author_email="malacaihiebert@gmail.com",
    license="MIT",
    classifiers=[
        "License :: OSI Approved :: MIT License",
        "Programming Language :: Python :: 3",
        "Programming Language :: Python :: 3.7",
        "Programming Language :: Python :: 3.8",
    ],
    packages=["hello"],
    include_package_data=True,
    
    # Only do this last part if your package contains third-party python packages
    install_requires=["requests, pygame"],
)
```

## 2. README.md
In here you write your documentation for you python package!
If you want to write your README file in plain text instead of markdown, do README.txt instead of README.md.

## 3. LICENSE
If you are using an MIT license copy text below, otherwise go to 'chooselicense.com'.
```
MIT License

Copyright (c) [year] [fullname]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 4. MANIFEST.in
Copy this text into your MANIFEST.in file.
```
include README.md LICENSE
```

## 5. '__init__.py'
```python
from hello.hello import *
```

# Publish to PyPI

## 1. Building Package
```
python setup.py sdist bdist_wheel
```

## 2. Check Distribution
```
twine check dist/*
```

## 3. Upload to PyPI
```
twine upload --repository-url https://upload.pypi.org/legacy/ dist/*
```
