# Distro contrainers

Containers for testing R packages on some popular Linux distributions using the native R installation for that distro. To run a container locally use:

```sh
docker run -it ghcr.io/r-devel/rocky-8
```

The containers are available for x86_64 and arm64, for the full list see: https://github.com/orgs/r-devel/packages?repo_name=containers


## Use on GitHub actions

Example workflow to test your R package on GitHub Actions with several distros and architectures:


```yaml
name: Linux Distros
on:
  push:
  pull_request:

jobs:
  rhel:
    runs-on: ubuntu-24.04${{matrix.arch=='arm64' && '-arm' || ''}}
    name: ${{ matrix.distro }} ${{ matrix.arch }}
    strategy:
      fail-fast: false
      matrix:
        distro: [ 'rocky-8', 'fedora' ]
        arch: [ 'amd64', 'arm64' ]
    container:
      image: ghcr.io/r-devel/${{ matrix.distro }}:latest
    steps:
      - uses: actions/checkout@v4
      - uses: r-lib/actions/setup-r-dependencies@v2
      - uses: r-lib/actions/check-r-package@v2
```

Copy this template into `.github/workflows/distros.yml` in your R package repository on GitHub.


## Other containers

There are many other people maintaining containers with R installations for different purposes:

  - [r-hub/containers](https://github.com/r-hub/containers): extensive collection of R configurations for testing R with various compilers and instrumatation tools.
  - [r-hub/r-minimal](https://github.com/r-hub/r-minimal): light weight R image based on alpine and musl libc.
  - [r-rocker](https://rocker-project.org/images/): images with various versions of R and preinstalled packages.

Use whatever works for you.