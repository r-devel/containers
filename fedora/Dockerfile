FROM fedora:latest

RUN \
  dnf upgrade -y &&\
  dnf install -y R-devel curl-devel && \
  dnf clean all

ENV R_LIB_FOR_PAK="/paklib"

RUN dnf install -y libsecret-devel curl-devel &&\
  mkdir "$R_LIB_FOR_PAK" &&\
  R -e "install.packages('pak', repos = c('https://r-lib.r-universe.dev', 'https://cloud.r-project.org'), '$R_LIB_FOR_PAK'); library(pak, lib.loc='$R_LIB_FOR_PAK')"

