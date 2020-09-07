![Binoculars](images/cygourgs.png)

[![Build Status](https://travis-ci.org/pySRURGS/cyGOURGS.svg?branch=master)](https://travis-ci.org/pySRURGS/cyGOURGS)
[![License: GPL v3](images/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![python versions](images/python-3_6_3_7-blue.svg)](https://www.python.org)

# Global Optimization by Uniform Random Global Search

This software package solves problems whose solutions can be represented as 
n-ary trees. These problems are typically solved using genetic programming. 
For these problems, there is often little to no relationship between the data
structure representation of a candidate solution and the ultimate performance of 
the candidate solution, once the data structure representation has been 
evaluated to its human readable form. This makes pure random search an 
attractive algorithm with which to solve these kinds of problems. This software 
is aimed at engineers, researchers and data scientists working in data analysis 
and computational optimization.

Users who are unfamiliar with GOURGS should refer to the 
python version of this same software [pyGOURGS](https://github.com/pySRURGS/pyGOURGS). 
This is a C++/Cython port of pyGOURGS created for improved performance.

## Features 

1. Developed and tested on C++11
2. Can be run in deterministic mode for reproducibility
3. Can also run an exhaustive/brute-force search
4. API is similar to that of the popular DEAP genetic programming software

## Installing

### On Ubuntu 18.04

1. Everything but the Boost C++ codes are preinstalled by your distribution. You can install boost using `sudo apt-get install libboost-dev`
2. Copy the repository to your computer and install using terminal: 
```
git clone https://github.com/pySRURGS/cyGOURGS.git
cd cyGOURGS
pip3 install -r requirements.txt --user
bash install.sh
```

### On Windows

Installation on Windows is a bit more involved.

1. Install a C++ compiler (gcc) using https://sourceforge.net/projects/mingw/
2. Install a terminal, I tend to use `git bash` https://gitforwindows.org/
3. Make sure the path to gcc is in your Environment Variables https://en.wikipedia.org/wiki/Environment_variable
4. Install the C++ boost library https://www.boost.org/users/history/version_1_72_0.html
5. Edit the `boost_path.py` file to point to the path of the Boost library. Follow the path formatting of the original example. Example: `path_to_boost="g:/c++_codes/boost_1_72_0"`
6. Copy the repository to your computer and install using terminal: 
```
git clone https://github.com/pySRURGS/cyGOURGS.git
cd cyGOURGS
pip3 install -r requirements.txt --user
bash install.sh
```

## Usage

Users of pyGOURGS are referred to the similarly named `ant.py` in `./cyGOURGS/examples/ant.py` which has an identical interface with the addition of the `cppimpl` flag, which uses the C++ cyGOURGS when `True` and which uses the python3 pyGOURGS when `False`. 

The manual page of the artificial ant problem solver can be generated by using `python3 ant.py -h`

```
usage: ant.py [-h] [-num_trees NUM_TREES] [-num_iters NUM_ITERS]
              [-freq_print FREQ_PRINT] [-deterministic DETERMINISTIC]
              [-exhaustive EXHAUSTIVE] [-multiprocessing MULTIPROCESSING]
              [-cppimpl CPPIMPL]
              output_db

positional arguments:
  output_db             An absolute filepath where we save results to a SQLite
                        database. Include the filename. Extension is typically
                        '.db'

optional arguments:
  -h, --help            show this help message and exit
  -num_trees NUM_TREES  pyGOURGS iterates through all the possible trees using
                        an enumeration scheme. This argument specifies the
                        number of trees to which we restrict our search.
                        (default: 10000)
  -num_iters NUM_ITERS  An integer specifying the number of search strategies
                        to be attempted in this run (default: 1000)
  -freq_print FREQ_PRINT
                        An integer specifying how many strategies should be
                        attempted before printing current job status (default:
                        10)
  -deterministic DETERMINISTIC
                        should algorithm be run in deterministic manner?
                        (default: False)
  -exhaustive EXHAUSTIVE
                        should algorithm be run in exhaustive/brute-force
                        mode? This can run forever if you are not careful.
                        (default: False)
  -multiprocessing MULTIPROCESSING
                        should algorithm be run in multiprocessing mode?
                        (default: False)
  -cppimpl CPPIMPL      should use cpp implementation of algorithms? (If True,
                        use C++ implementation. Else if False, use pyGOURGS
                        python implementation.) (default: True)
```

## Authorship

Port from Python to Cython/C++ performed by Razvan Tarnovan in collaboration with Sohrab Towfighi.

Copyright belongs to Sohrab Towfighi.

## License

This project is licensed under the GPL 3.0 License - see the [LICENSE](LICENSE.txt) file for details

## How to Cite

If you use this software in your research, then please cite us.

Towfighi, S., (2020). pyGOURGS - global optimization of n-ary tree representable problems using uniform random global search. Journal of Open Source Software, 5(47), 2074, https://doi.org/10.21105/joss.02074

## Community

If you would like to contribute to the project or you need help, then please create an issue.

With regards to community suggested changes, I would comment as to whether it would be within the scope of the project to include the suggested changes. If both parties are in agreement, whomever is interested in developing the changes can make a pull request, or I will implement the suggested changes.

## Acknowledgments

* The example scripts are derived from the DEAP project: [link](https://github.com/DEAP/deap)
* Luther Tychonievich created the algorithm mapping integers to full binary trees: [link](https://www.cs.virginia.edu/luther/blog/posts/434.html), [web archived link](http://web.archive.org/web/20190908010319/https://www.cs.virginia.edu/luther/blog/posts/434.html).
* The icon is derived from the GNOME project and the respective artists. Taken from [link](https://commons.wikimedia.org/wiki/File:Gnome-system-run.svg), [web archived link](https://web.archive.org/web/20161010072611/https://commons.wikimedia.org/wiki/File:Gnome-system-run.svg). License: LGPL version 3.0. 

## References

- Koza JR, Koza JR. Genetic programming: on the programming of computers by means of natural selection. MIT press; 1992.
- Towfighi S. Symbolic regression by uniform random global search. SN Applied Sciences. 2020 Jan 1;2(1):34. [https://doi.org/10.1007/s42452-019-1734-3](https://doi.org/10.1007/s42452-019-1734-3)
