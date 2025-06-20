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

COPY Renviron /usr/lib64/R/etc/Renviron.site
#COPY Renviron /opt/R/4.5.1/lib/R/etc/Renviron.site
