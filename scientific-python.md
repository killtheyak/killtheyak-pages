title: Install a scientific Python environment (numpy + scipy + matplotlib) on MacOSX without Enthought
updated: 2013-07-14 13:30:00
os: [macosx]
tags: [python, scientific]
deps: [install-homebrew, install-python, install-mac-xcode-compilers]
contributors: ["http://www.github.com/sloria"] 
description: Python has many excellent libraries for scientific computing. Unfortunately, installing these libraries can be a yak shaving nightmare. One solution is to download the Enthought Python Distribution, a Python distribution that comes bundled with a large number of packages precompiled. While the EPD may be the best solution to get off the ground with scientific computing in as little time as possible, problems may arise when (1) you want to use python outside of the EPD environment, possibly with diffent Python versions and (2) you want to keep your scientific environment in a virtualenv.

## Optional (but recommended) first step: Create a new virtual environment

```bash
# If you're using virtualenvwrapper
$ mkvirtualenv science
$ workon science
```

## Numpy, Scipy, and Matplotlib

Install a fortran compiler and Freetype.

```bash
$ brew update
$ brew install gfortran freetype
# Remember to follow any instructions that show up after each install
# To display the instructions again, run `brew info gfortran` or `brew info freetype`
```

Install the Python packages.

```bash
# Order matters!
$ pip install numpy
$ pip install scipy
$ pip install matplotlib
# Optional: install ipython
$ pip install ipython
```

If everything works, you should be able to `import pylab`, which will bring numpy, scipy, and matplotlib functionality all in one go.

```bash
# Check that everything works
$ python
>>> import pylab
```

If all you need is numpy, scipy, and matplotlib, you're done!

## Bonus: Install the rest of the EPD packages

If you want to install more of the libraries included with EPD, you can try making a `requirements.txt` file containing the following:

```bash
# requirements.txt
# This includes all the packages bundled with EPD-Free
# Feel free to add/remove any items
appinst>=2.1.1
apptools>=4.1.0
casuarius>=1.0
chaco>=4.2.0
cloud>=2.4.6
configobj>=4.7.2
distribute>=.6.26
enable>=4.2.0
enaml>=0.2.0
enstaller>=4.5.1
etsproxy>=0.1.1
freetype>=2.4.4
ipython>=0.12.1
jinja2>=2.6
libjpeg>=7.0
libpng>=7.0
matplotlib>=1.1.0
nose>=1.1.2
numpy>=1.6.1
PIL>=1.1.7
ply>=3.4
pyaudio>=0.2.4
pyface>=4.2.0
pyglet>=1.1.4
pygments>=1.4
python_dateutil>=1.5
pytz
pyzmq>=2.1.11
scipy>=1.74
tornado>=2.2
traits>=4.2.0
traitsui>=4.2.0
wxPython>=2.8.10
```

Then run:

```bash
$ pip install -r -U requirements.txt
```

NOTE: This step has not been verified. It is possible that some of the packages have other non-Python dependencies that need to be installed first.

See also:

- [Enthought Python Distribution][EPD]
- [Installing scientific Python on MacOS X - Lowin Data Company](http://www.lowindata.com/2013/installing-scientific-python-on-mac-os-x/)

[EPD]: https://www.enthought.com/products/epd/
[virtualenv]: /use-virtualenvwrapper