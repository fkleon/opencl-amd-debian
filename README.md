# Debian packaging script for opencl-amd

> OpenCL userspace driver as provided in the amdgpu-pro driver stack. This package is intended to work along with the free amdgpu stack.

Bash implementation using the [opencl-amd AUR pkgbuild](https://aur.archlinux.org/packages/opencl-amd/)
to build a DEB package for `opencl-amd`.

## Build requirements

You need `wget` and `docker` (to run [fpm](https://github.com/jordansissel/fpm)).

Build the required FPM docker image with:

    docker build -t fpm:1.12.0 .

## Usage

Run the build script:

    ./opencl-amd-debian

The script performs the following steps:
- download the current upstream pkgbuild
- download and verify the sources
- build the package root with upstream instructions
- create a DEB package with fpm in Docker

The resulting DEB package is saved as `./build/opencl-amd_${pkgver}_amd64.deb`.

### Packaging an older version

If you wish to package an older version of the amdgpu-pro driver, you can
override the pkgbuild via the `PKGBUILD_SRC` environment variable, for example
to the 20.40 stable link as described [in AUR](https://aur.archlinux.org/packages/opencl-amd/#pinned-776514).
