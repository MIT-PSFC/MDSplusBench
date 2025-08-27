# Custom HDF5 Build for Benchmarking new ROS3 Backend

The build process followed the instructions in this HDF5 blog: https://www.hdfgroup.org/2025/07/22/how-to-build-hdf5-library-and-h5py-in-a-conda-virtual-environment-update/. Below are the build artifacts used:

* User CMake preset file [CMakeUserPresets.json](./CMakeUserPresets.json) with
  the `my-MDSplus-bench` preset.
* Conda environment list of installed packages. Some of the packages are kept at
  the same version as the old ROS3 backend'a environment.

  ```yaml
  channels:
    - conda-forge
  dependencies:
    - numpy=2.2.0
    - aws-c-s3
    - dask=2024.12.1
    - dask-core=2024.12.1
    - dask-expr=1.1.21
    - pandas=2.2.3
    - pip
    - python=3.12.8
    - setuptools
    - cython
    - wheel
    - s3fs=2024.10.0
    - cmake
    - ninja
    - c-compiler
  ```

* CMake command for building the HDF5 library from source code. The test
  (optional) and install commands are the same as in the above mentioned blog.

  ```
  $ cmake \
      --preset my-MDSplus-bench \
      -S . \
      -B ../build \
      -G Ninja \
      -DCMAKE_INSTALL_PREFIX=${CONDA_PREFIX}
  ```

* Build from source and install h5py using the custom-built HDF5 library. The
  h5py version is the same as in the original benchmark conda environment with
  the old ROS3 backend.

  ```
  $ HDF5_DIR=$CONDA_PREFIX python -m pip install \
      --no-binary=h5py \
      --no-build-isolation \
      "h5py==3.12.1"
  ```
