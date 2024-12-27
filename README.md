# PYBAG

Python wrapper for [cbag](https://github.com/ucb-art/cbag) library for BAG3++.

Pybag provides `enum.py` and `core.pyi` as an interface between `BAG` and `cbag`. 
`core.pyi` is created during `cbag` compilation and is not tracked by Git.

## Setup

This library should be used with [BAG3++](https://github.com/ucb-art/bag). To setup BAG, follow the instructions outlined on the [RTD page](https://bag3-readthedocs.readthedocs.io/en/latest/dependencies/).

Alternative, if you are using Ubuntu, you can use the `setup_script.sh` under the `setup` directory. This runs the steps described in the RTD page above. See the `setup/README.md` for discussion.

To build the `pybag` library, run `./run_test.sh`. This will compile `cbag` as well as create the `pybag` Python wrappers for `BAG`.

Running `./run_test.sh`requires the `PYBAG_PYTHON` environment variable be set to the Python from your Miniconda install from the setup process.

### Tool Build Dependencies
- autoconf
- curl
- gcc
- g++
- git
- libgl1-mesa-dev - for CMake Qt depencies
- libtool
- libtool-dev
- pkg-config
- make

### C++ Build Dependencies
- cmake
- magic-enum
- yaml-cpp
- libfyaml
- HDF5
- Boost

### Build Dependencies from Conda
- spdlog=1.9.1, fmt=8.0.1
- setuptools
- qt, pyqt
- zlib, zstd

### Building with OpenAccess Libraries

Pybag (and the underlying cbag) can be compiled with the OpenAccess (OA) C++ libraries from Si2 to provide minor acceleration in creating OA views for tools such as Cadence Virtuoso. These libraries are **NOT required** for using BAG in general. If the OA libraries are not included, BAG can still create OA views using SKILL commands.

To compile with these libraries, the following environment variables must be set:
- `OA_INCLUDE_DIR`: Include directory.
- `OA_LINK_DIR`: Link directory.

Compiling with the OA libraries will add the `PyOADatabase` class to `core.pyi` after compile time. If `PyOADatabase` does not exist, then you did not compile with the OA libraries.

Pybag has been tested with the OpenAccess 2.2 API. These features are included for legacy compatibility and are not actively maintained.

## Licensing

This library is licensed under the Apache-2.0 license.  However, some source files are licensed
under both Apache-2.0 and BSD-3-Clause license, meaning that the user must comply with the
terms and conditions of both licenses.  See [here](LICENSE.BSD-3-Clause) for full text of the
BSD license, and [here](LICENSE.Apache-2.0) for full text of the Apache license.  See individual
files to check if they fall under Apache-2.0, or both Apache-2.0 and BSD-3-Clause.
