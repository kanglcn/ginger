# Decorrelation

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

> A InSAR postprocessing tool in big data era

This package provide functions for InSAR post-processing which refers as
processing after SAR images co-registration and geocoding. The functions
include PS/DS identification, coherence matrix estimation, phase linking
etc.

## What make Decorrelation different?

- Decorrelation implements state-of-art InSAR techniques. Currently it
  includes advanced PS/DS identification, phase linking and
  deep-learning-based methods that performs much better than the classic
  one.
- Decorrelation runs fast. As many of InSAR processing are pixel-wise or
  patch-wise manipulation, Most of Decorrelation functions are
  implemented with well-optimized GPU code. Furthermore, with the
  support of [Dask](https://docs.dask.org/en/stable/), Decorrelation can
  be runed on multi-GPUs to further accelerate the processing and get
  rid of the limitation of GPU memory.
- Decorrelation support interative big data visulization. Since the SAR
  data volume increase dramatically recently and in near future, not
  only the processing time is a concern (which is largely solved as
  Decorrelation runs so fast!), the inspection on the images is a
  problem. Decorrelation provide
  [Datashader](https://datashader.org/index.html)-based functions for
  accurate, interative representation on even largest time series InSAR
  data.

Please refer to the
[Documentation](https://kanglcn.github.io/decorrelation) for detailed
usage.

<div>

> **Warning**
>
> Due to the heavy dependence on CuPy and CUDA, this package only works
> on device with Nivida GPU.

</div>

<div>

> **Warning**
>
> This package is under intensive development. API is subjected to
> change without any noticement.

</div>

## Install

Because of GPU driver and CUDA Version Compatibility, there is no simple
solution for CUDA related packages installation. Users need to
successfully install
[cupy](https://docs.cupy.dev/en/stable/install.html#installation) and
[dask_cuda](https://docs.rapids.ai/api/dask-cuda/stable/) first.

Here is some tips for installing them. Generally, the cuda driver is
alrealy installed and maintained by the system administrator. Users only
need to determine the right cudatoolkit version. Frist run

``` bash
nvidia-smi
```

It will prints something like:

    ...
    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 525.105.17   Driver Version: 525.105.17   CUDA Version: 12.0     |
    |-------------------------------+----------------------+----------------------+
    ...

The `CUDA Version` is the maxminum cudatoolkit version that supported by
the current CUDA driver. Here we use version 11.8 as an example. Then
you can install the needed `cudatoolkit`, `cupy`, `dask_cuda` by:

``` bash
conda install -c "nvidia/label/cuda-11.8.0" cuda-toolkit
conda install -c conda-forge cupy cuda-version=11.8
conda install -c rapidsai -c conda-forge -c nvidia dask-cuda cuda-version=11.8
```

Then

With conda:

``` bash
conda install -c conda-forge decorrelation
```

Or with pip:

``` bash
pip install decorrelation
```

In development mode:

``` bash
git clone git@github.com:kanglcn/decorrelation.git ./decorrelation
cd ./decorrelation
pip install -e '.[dev]'
```

## How to use

Read the [software
architecture](./Introduction/software_architecture.ipynb) first.

## Contact us

- Most discussion happens on
  [GitHub](https://github.com/kanglcn/decorrelation). Feel free to [open
  an issue](https://github.com/kanglcn/decorrelation/issues/new) or
  comment on any open issue or pull request.
- use github
  [discussions](https://github.com/kanglcn/decorrelation/discussions) to
  ask questions or leave comments.

## Contribution

- Pull requests are welcomed! Before making a pull request, please open
  an issue to talk about it.
- We have notice many excellent open-source packages are rarely paid
  attention to due to lack of documentation. The package is developed
  with the [nbdev](https://nbdev.fast.ai/), a notebook-driven
  development platform. Developers only need to simply write notebooks
  with lightweight markup and get high-quality documentation, tests,
  continuous integration, and packaging automatically.
