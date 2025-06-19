FROM rockylinux/rockylinux:8

RUN \
  dnf upgrade -y && \
  dnf install -y dnf-plugins-core epel-release && \
  dnf config-manager --set-enabled powertools epel-testing &&\
  dnf install -y R-devel curl-devel gawk make patch pkg-config langpacks-en qpdf && \
  dnf clean all
