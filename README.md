# Distro contrainers

Containers for testing R and packages on some popular Linux distributions. To run a container locally use:

```sh
docker run -it ghcr.io/r-devel/rocky-8
```

The containers are available for x86_64 and arm64, for the full list see: https://github.com/orgs/r-devel/packages?repo_name=containers

### Other containers

There are many other people maintaining containers with R installations for all kinds of purposes:

  - [r-hub/containers](https://github.com/r-hub/containers): special R configurations for testing with various compilers and instrumatation.
  - [r-hub/r-minimal](https://github.com/r-hub/r-minimal): light weight R image based on alpine and musl libc.
  - [r-lib/rig](https://github.com/r-lib/rig?tab=readme-ov-file#all-containers): containers with R builds from Posit on various distros.
  - [r-rocker](https://rocker-project.org/images/): images with various versions of R and preinstalled packages.

Use whatever works for you.

## Using containers on GitHub actions

Below an example workflow to test an R package on GitHub Actions on multiple containers and architectures.


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
        distro: [ 'rocky-8', 'rocky-9', 'fedora' ]
        arch: [ 'amd64', 'arm64' ]
    container:
      image: ghcr.io/r-devel/${{ matrix.distro }}:latest
    steps:
      - uses: actions/checkout@v4
      - uses: r-lib/actions/setup-r-dependencies@v2
        with:
          extra-packages: any::rcmdcheck
          needs: check
      - uses: r-lib/actions/check-r-package@v2
```

Adapt to your needs and copy the template into e.g. `.github/workflows/distros.yml` in your R package repository on GitHub.
