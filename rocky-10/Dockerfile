# EXPERIMENTAL: R-devel requires Rocky >= 10.1 and rig also does not support Rocky yet
# so for now we use CentOS stream.

# FROM rockylinux/rockylinux:10
FROM quay.io/centos/centos:stream10

RUN \
  dnf upgrade -y && \
  dnf install -y dnf-plugins-core epel-release &&\
  dnf config-manager --set-enabled epel-testing crb &&\
  dnf install -y R-devel curl-devel gawk make patch pkg-config langpacks-en && \
  dnf clean all
