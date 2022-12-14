# Docker-powered Repast HPC development environment
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![License: CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc/4.0/)
![GitHub last commit](https://img.shields.io/github/last-commit/W-Mohammed/docker-repast-hpc?color=red&style=plastic)
![GitHub downloads](https://img.shields.io/github/downloads/W-Mohammed/docker-repast-hpc/total?style=plastic)
![GitHub top language](https://img.shields.io/github/languages/top/W-Mohammed/docker-repast-hpc?style=plastic)
![GitHub repo size](https://img.shields.io/github/repo-size/W-Mohammed/docker-repast-hpc?style=plastic)
[![GitHub forks](https://img.shields.io/github/forks/W-Mohammed/docker-repast-hpc?style=social&label=Fork&maxAge=2592000)](https://GitHub.com/W-Mohammed/docker-repast-hpc/network/)

- **[Introduction](#introduction)**
- **[Usage](#usage)**
- **[Build](#build)**
- **[Contact](#contact)**
- **[Changelog](#changelog)**

## Introduction:
This repo contains the dockerfiles housing the instructions to generate docker-powered [Repast for High-Performance Computing](https://repast.github.io/repast_hpc.html) (**Repast HPC**) development environments.

The current Repast HPC version supported by the docker images is 2.3.1; whereas we used ubuntu 22.10 and alpine 3.16.2 as the base images in the dockerfiles.

## Usage:
### To pull (download) any of the images:
Make sure you have Docker Engine on your machine and run one of the following commands.

`# Ubuntu.22.10-powered image:`
```powershell
docker pull ghcr.io/w-mohammed/repast-hpc:2.3.1-ubuntu22.10-v1.2
```
`# alpine3.16.2-powered image:`
```powershell
docker pull ghcr.io/w-mohammed/repast-hpc:2.3.1-alpine3.16.2
```

### To run the Repast HPC development environment mapping a working directory: 
This image is primarily intended as a development environment that the user can employ to develop their Agent-Based Models (ABM)s. To get started with your development: 
- navigate to your projects working directory (where your model files are or are to be saved), and
- run one of the commands below (depending on which Linux distribution you prefer to work with and the image you pulled earlier).

#### Linux users:
`# Ubuntu.22.10-powered image:`
```powershell
docker run --rm -it -v $(pwd):/project/mounted ghcr.io/w-mohammed/repast-hpc:2.3.1-ubuntu22.10-v1.2
```
`# alpine3.16.2-powered image:`
```powershell
docker run --rm -it -v $(pwd):/project/mounted ghcr.io/w-mohammed/repast-hpc:2.3.1-alpine3.16.2
```
#### Windows users (PowerShell):
`# Ubuntu.22.10-powered image:`
```powershell
docker run --rm -it -v ${PWD}:/project/mounted ghcr.io/w-mohammed/repast-hpc:2.3.1-ubuntu22.10-v1.2
```
`# alpine3.16.2-powered image:`
```powershell
docker run --rm -it -v ${PWD}:/project/mounted ghcr.io/w-mohammed/repast-hpc:2.3.1-alpine3.16.2
```

### To use the images as base layers in a dockerfile:
It is also possible to use any of the supported images as a base layer in other dockerfiles. 

`# Ubuntu.22.10-powered image:`
```dockerfile
FROM ghcr.io/w-mohammed/repast-hpc:2.3.1-ubuntu22.10-v1.2
```
`# alpine3.16.2-powered image:`
```dockerfile
FROM ghcr.io/w-mohammed/repast-hpc:2.3.1-alpine3.16.2
```

## Build:
Users can build any of the images from hosted dockerfiles:
- clone the repository using `git clone https://github.com/W-Mohammed/docker-repast-hpc.git`,
- navigate to the `docker-repast-hpc` folder, and 
- of the two commands below, call the one that corresponds to the linux distribution in which you are interested.

`# Ubuntu.22.10-powered image:`
```powershell
docker build --tag repast-hpc ./ubuntu
```
`# alpine3.16.2-powered image:`
```powershell
docker build --tag repast-hpc ./alpine
```

## Contact:
[Wael Mohammed](https://www.linkedin.com/in/wael-mohammed/)

*Public Health Economics and Decision Science, Wellcome Trust Doctoral Training Center, ScHARR, University of Sheffield, UK*

Contact:   wmamohammed1@sheffield.ac.uk

## Changelog:
### `ubuntu`-based image [v.1.2] - 2022-10-05
#### Removed:
- The `ldconfig` command from the dockerfile.
#### Added:
- In the previous version `build-essential` was removed when building the docker image. However, since it could be useful to prospective users, it is now left in docker image and respective removal commands were omitted from the source dockerfile.
