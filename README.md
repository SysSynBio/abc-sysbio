
This is a fork of the Python package ``abc-sysbio``.
Compared to the [official ABC-SysBio release](http://www.theosysbio.bio.ic.ac.uk/resources/abc-sysbio/), this fork has been significantly refactored, and all of the simulation code has been moved into [my fork of cuda-sim](https://github.com/jamesscottbrown/cuda-sim) (which derives from the [last official cuda-sim release](https://sourceforge.net/projects/cuda-sim/)).
**It is still somewhat experimental, and there may be bugs that were introduced in the refactoring and not yet been found**.



``abc-sysbio`` implements likelihood free parameter inference and model selection in dynamical systems.

It is designed to work with both stochastic and deterministic models written in [Python](https://www.python.org/) or [Systems Biology Markup Language](http://sbml.org) (SBML).

``abc-sysbio`` combines three algorithms: ABC rejection sampler, ABC SMC for parameter inference and ABC SMC for model selection.


# Contents

* [Prerequisites](#user-content-prerequisites)
* [Linux installation](#user-content-linux-installation)
* [Mac OS X installation](#user-content-mac-os-installation)

# Prerequisites

Before trying to install and use abc-sysbio you must
first install the following packages

    numpy
    matplotlib
    libSBML (SBML interface)
    scipy (ODE models)
    cuda-sim (Nvidia GPU)

While the first two are essential, the latter three need only
be installed if full use of abc-sysbio is required.


You can then install in the usual way by downloading the code, changing directory, and running ``python setup.py install``.

# Linux installation

If custom installation is required then replace ``<dir>`` with the full path to a location. This will be the location containing lib and bin directories (usually ``/usr/local`` by default).

The ``--prefix=<dir>`` option is recommended since it will guarantee that each package picks up the correct dependency.

These instructions are for old versions of packages and the newest versions should be used in their place.

If the target  ``<dir>`` is write protected, the user may need to use ``sudo make install`` instead of ``make install``.

1) Download and install [python](http://www.python.org/ftp/python/2.6.5/Python-2.6.5.tgz)
    
    tar xzf Python-2.6.5.tgz
    cd Python-2.6.5
    ./configure --prefix=<dir> --enable-shared
    make
    make install

Make sure this new version of python is picked up by default
    
    export PATH=<dir>/bin:$PATH  (for BASH)
    setenv PATH <dir>/bin:$PATH

2) Download and install [numpy](http://downloads.sourceforge.net/project/numpy/NumPy/1.4.1rc2/numpy-1.4.1rc2.tar.gz)
    
    tar xzf numpy-1.4.1rc2.tar.gz    
    cd numpy-1.4.1rc2
    python setup.py install --prefix=<dir>

3) Download and install [matplotlib](http://downloads.sourceforge.net/project/matplotlib/matplotlib/matplotlib-0.99.1/matplotlib-0.99.1.2.tar.gz)

    tar xzf matplotlib-0.99.1.2.tar.gz
    cd matplotlib-0.99.1.1/    
    python setup.py build
    python setup.py install --prefix=<dir>

4) Download and install [swig](http://downloads.sourceforge.net/project/swig/swig/swig-1.3.40/swig-1.3.40.tar.gz).
Note that this is required by libsbml and it must be at least version 1.3.39

    tar -xzf swig-1.3.40.tar.gz
    cd swig-1.3.40
    ./configure --prefix=<dir>
    make
    make install

5) Download and install [libSBML](http://downloads.sourceforge.net/project/sbml/libsbml/4.0.1/libsbml-4.0.1-src.zip)

    unzip libsbml-4.0.1-src.zip
    cd libsbml-4.0.1    
    ./configure --with-python=<dir> --prefix=<dir> --with-swig=<dir>
    make 
    make install

6) Download and install [scipy](http://downloads.sourceforge.net/project/scipy/scipy/0.7.2rc2/scipy-0.7.2rc2.tar.gz)

Note that scipy requires [ATLAS](http://math-atlas.sourceforge.net/)
but should be included in most linux distributions. You need to locate
the ATLAS libraries

    tar xzf scipy-0.7.2rc2.tar.gz
    cd scipy-0.7.2rc2
    export ATLAS=/full/path/to/atlas/libraries
    python setup.py build
    python setup.py install --prefix=<dir>

7) Download and install cuda-sim (optional)

8) Install abc-sysbio
In the unzipped abc-sysbio package directory do
   
    python setup.py install --prefix=<dir>

This places the abcsysbio package into 
     
    <dir>/lib/python2.6/site-packages/

and writes the scripts
    
    <dir>/bin/abc-sysbio-sbml-sum
    <dir>/bin/run-abc-sysbio

Add the script directory to the path (must be done in each session or added to .bashrc or .cshrc file)

    export PATH=<dir>/bin:$PATH  (bash shells)
    setenv PATH <dir>/bin:$PATH  (c shells)

Then  the command

    run-abc-sysbio -h

should display a list of options and you are ready to run the examples.


# Mac OS installation

It is recommended that you install Python/Numpy/Matplotlib together using the [Scipy Superpack](http://fonnesbeck.github.io/ScipySuperpack/),
[Enthought Canopy](https://www.enthought.com/products/canopy/) or [Anaconda](https://www.continuum.io/downloads).

You can then install libSBML using [these instructions](http://sbml.org/Software/libSBML/docs/python-api/libsbml-downloading.html#dl-python)

Download the [ABC-SysBio package](https://github.com/jamesscottbrown/abc-sysbio/releases/) and unzip it. Open a terminal and type:

     cd abc-sysbio-2.07
     sudo python setup.py install 

This places the ABC-SysBio package into 

     /Library/Python/2.7/site-packages/

and writes the scripts

     /usr/bin/abc-sysbio-sbml-sum
     /usr/bin/run-abc-sysbio

Then the command

     run-abc-sysbio -h

will display a list of options and you are ready to run the examples.
