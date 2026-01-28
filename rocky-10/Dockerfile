# Sometimes R-devel requires more recent stuff and you need centos-stream
# FROM quay.io/centos/centos:stream10
FROM rockylinux/rockylinux:10

RUN \
  dnf upgrade -y && \
  dnf install -y dnf-plugins-core epel-release &&\
  dnf config-manager --set-enabled epel-testing crb &&\
  dnf install -y R-devel curl-devel gawk make patch pkg-config langpacks-en && \
  dnf clean all

COPY Renviron /usr/lib64/R/etc/Renviron.site
#COPY Renviron /opt/R/4.5.2/lib/R/etc/Renviron.site
