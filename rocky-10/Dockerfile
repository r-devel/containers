# R-devel requires Rocky >= 10.1 so for now we use CentOS stream until Rocky 10.1 is available
# FROM rockylinux/rockylinux:10

FROM quay.io/centos/centos:stream10

RUN \
  dnf upgrade -y && \
  dnf install -y dnf-plugins-core epel-release &&\
  dnf config-manager --set-enabled epel-testing crb &&\
  dnf install -y R-devel curl-devel && \
  dnf clean all

ENV R_LIB_FOR_PAK="/paklib"

RUN dnf install -y libsecret-devel curl-devel &&\
  mkdir "$R_LIB_FOR_PAK" &&\
  R -e "install.packages('pak', repos = c('https://r-lib.r-universe.dev', 'https://cloud.r-project.org'), '$R_LIB_FOR_PAK'); library(pak, lib.loc='$R_LIB_FOR_PAK')"

