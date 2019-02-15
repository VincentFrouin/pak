
<!-- README.md is generated from README.Rmd. Please edit that file -->

# pak

> Manage Package
Libraries

<!-- badges: start -->

![lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg)
[![Linux Build
Status](https://travis-ci.org/r-lib/pak.svg?branch=master)](https://travis-ci.org/r-lib/pak)
[![Windows Build
status](https://ci.appveyor.com/api/projects/status/4sir94ye38nwgxpx/branch/master?svg=true)](https://ci.appveyor.com/project/gaborcsardi/pak)
[![](https://www.r-pkg.org/badges/version/pak)](https://cran.r-project.org/package=pak)
[![CRAN RStudio mirror
downloads](https://cranlogs.r-pkg.org/badges/pak)](https://www.r-pkg.org/pkg/pak)
[![Coverage
Status](https://img.shields.io/codecov/c/github/r-lib/pak/master.svg)](https://codecov.io/github/r-lib/pak?branch=master)
<!-- badges: end -->

pak installs R packages from various sources.

## Installation

Install the package from CRAN:

``` r
install.packages("pak")
pak::pak_create_private_lib()
```

The second line creates pak’s own package library, to avoid interference
between pak’s dependencies and the user’s regular packages. Run this
command any time to update pak’s package library.

## Usage

Simply call `pkg_install` to install packages:

``` r
pak::pkg_install("dplyr", lib = "/tmp/lib")
```

All dependencies will be installed as well, to the same library.

## Goals

  - Make package installation cheaper and more reliable.

  - Cheaper, reliable package installation allows safer, more convenient
    workflows.

## Features

### Speedy Features

  - Fast downloads and queries (all HTTP is concurrent).

  - Fast installs (package installations and builds are concurrent).

  - Package cache (all downloaded and locally built packages are
    cached).

  - Lazy downloads, only download metadata and package files if needed.

### Safety features

  - Private library (pak’s own dependencies do not affect your “regular”
    packages and vice versa).

  - Do not load any package in the main process (except for pak itself).
    Every operation runs in the sub-process, and the packages are loaded
    from the private library.

  - Dependency solver: makes sure that you end up in a consistent,
    working state of dependencies. Find conflicts up front, before
    actually installing anything.

  - Confirmation, warning for overwriting loaded packages.

  - Concurrency safe, locks library, locks caches. Lock is released when
    the process terminates.

### Convenience features

  - GitHub packages.

  - BioC packages.

  - Show download sizes.

## License

GPL-3 © RStudio
