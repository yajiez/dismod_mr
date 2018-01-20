# Install Guides for macOS User

## Create a new Python Environment

```sh
conda create -n dismod-mr python=3 ipykernel
source activate dismod-mr
python -m ipykernel install --user --name dismod-mr --display-name "DisModel MR"
```

## Install the Requirements

```sh
pip install numpy
pip install scipy
pip install pandas
pip install networkx
pip install pymc
```

**For the PyCPPAD**

First install cppad using `brew`:

```sh
brew install cppad
```

Then we need to install `boost` and `boost-python`:

```sh
brew install boost --with-python
brew install boost-python
```

Using `brew list | grep 'boost'` to make sure you have them installed.

Now it's time to install the PyCPPAD, first clone the source code from the GitHub:

```sh
git clone https://github.com/b45ch1/pycppad.git
cd pycppad
```

An important thing is to modify the **setup variables** in the file `setup.py` to agree with your own system:

```python
# BEGIN USER SETTINGS
# Directory where CppAD include files are located
# cppad_include_dir        = [ '/usr/include' ]
cppad_include_dir        = [ '/usr/local/include/cppad/' ]
#
# Directory where Boost Python include files are located
boost_python_include_dir = [ '/usr/local/include/boost/python/' ]
#
# Director whre Boost Python library is located
# boost_python_lib_dir     = [ '/usr/lib' ] 
boost_python_lib_dir     = [ '/usr/local/lib' ] 
#
# Name of the Boost Python library in boost_python_lib_dir.
# boost_python_lib         = [ 'boost_python-mt' ]
boost_python_lib         = [ 'libboost_python' ]
# END USER SETTINGS
```

Then follow the instruction here:

http://www.seanet.com/~bradbell/pycppad/install.htm

## Install the `dismod_mr`

```sh
python setup.py install
```

