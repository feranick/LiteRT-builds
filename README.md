# LiteRT-builds
LiteRT cross-platform builds

## Why this repo?

The information provided in the [official LiteRT page for building `whl` packages ](https://ai.google.dev/edge/litert/build/cmake_pip) to cross-compile TFlite for different architectures is a good start. However there seem to be several issues. This repo aims at providing more info towards successful compilation. And some binaries as well. 

## Get and Initialize the source

- Install docker:

##
    sudo apt install docker.io

- Download tensorflow and checkout the relevant version.

##
    git clone https://github.com/google-ai-edge/LiteRT.git
##
    cd liteRT
##
   git submodule init && git submodule update
   
From the folder `third_party/tensorflow`, run one of the selected build scripts:

- Compile natively using Bazel:

```../../ci/build_pip_package_with_bazel.sh ```

- Native compilation with Docker + Bazel:

```../../ci/build_pip_package_with_docker.sh ```

- Cross-compilation with Docker + Bazel:

```make -C tensorflow/lite/tools/pip_package docker-build \
  TENSORFLOW_TARGET=<target> PYTHON_VERSION=<python3 version> ```
  
These are the supported targets.

- `armhf`:  ARMv7 VFP with Neon Compatible with Raspberry Pi 3 and 4
- `rpi0`: ARMv6 Compatible with Raspberry Pi Zero
- `aarch64`: aarch64 (ARM 64-bit) Coral Mendel Linux 4.0 or Raspberry Pi with Ubuntu Server 20.04.01 LTS 64-bit of 22.04.x LTS 64-bit
- `native`: 	Your workstation 	It builds with "-mnative" optimization  


## Note:
that the scripts:

`tensorflow/lite/tools/pip_package/Dockerfile.py3` and `tensorflow/lite/tools/pip_package/Makefile`

 may need to be changed according to the documentation for (`TFlite-builds`)[https://github.com/feranick/TFlite-builds]


