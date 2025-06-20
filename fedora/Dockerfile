FROM fedora:latest

RUN \
  dnf upgrade -y &&\
  dnf install -y R-devel curl-devel gawk make patch pkg-config langpacks-en qpdf && \
  dnf clean all

# Remove this when fixed: https://github.com/r-lib/pak/issues/787
RUN \
  yum install -y https://github.com/r-lib/rig/releases/download/latest/r-rig-latest-1.$(arch).rpm && \
  rig add 4.5.1 --without-pak

ENV PATH="/opt/R/4.5.1/bin:${PATH}"

COPY Renviron /usr/lib64/R/etc/Renviron.site
COPY Renviron /opt/R/4.5.1/lib/R/etc/Renviron.site

