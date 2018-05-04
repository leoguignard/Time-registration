# Time-registration

This repository contains the time registration script proposed in our Mouse-Atlas article.

## Description of the repository
Folders:
  - IO: The class `SpatialImage`, a container for images and input/output. When the right external libraries are installed (see bellow), can read tiff, hdf5, klb and inr images.
  - BlockMatching: the C code for spatial registration from (https://gitlab.inria.fr/greg/Klab-BlockMatching)
  - csv-parameter-files: Example of parameterization csv file for standalone-registration.py.

Python files:
  - standalone-registration.py: python script to register in time a time-series of 3D intensity images

## Basic usage
The python scripts proposed here can be run from a terminal in the following way:

`python standalone-registration.py`

The user is then prompted to provide a parameter csv file (examples provided in the folder csv-parameter-files). The path to the parameter file should then be typed in the terminal.

## Quick install
To quickly install the script so it can be call from the terminal and install too the common dependecies one can run
```shell
python setup.py install [--user]
```
Still will be remaining to install blockmathcing and IO packages.

## Dependencies
Some dependencies are required:
  - general python dependencies:
    - numpy, scipy, pandas
  - IO:
    - libtiff0-4-0 or later version
    - pyklb (https://github.com/bhoeckendorf/pyklb)
    - pyh5
  - standalone-registration.py:
    - blockmatching installed such that it can be called in a terminal as > blockmatching -ref [...] (https://gitlab.inria.fr/greg/Klab-BlockMatching)
    - IO library has to be installed and included in PYTHONPATH so it can be called in python as `from IO import imread` for example
    - psutil python library (can be installed using `pip install psutil` for example)
    - scikit-image (can be installed using `pip install scikit-image` for example)

Similarly, to include the IO library in the python path one can use the following command in a terminal:
  - For Ubuntu: `echo 'export PYTHONPATH=/path/to/IO:$PYTHONPATH' >> ~/.bashrc`
  - For MacOs: `echo 'export PYTHONPATH=/path/to/IO:$PYTHONPATH' >> ~/.profile`

