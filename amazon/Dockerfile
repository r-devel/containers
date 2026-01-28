FROM amazonlinux

RUN \
  dnf upgrade -y && \
  dnf install -y R-devel curl-devel gawk make patch pkg-config tar gzip langpacks-en && \
  dnf clean all

RUN \
  curl -sSL https://cdn.posit.co/r/rhel-9/pkgs/R-4.5.2-1-1.$(uname -m).rpm -o R-4.5.2.rpm && \
  rpm -i R-4.5.2.rpm && \
  rm  R-4.5.2.rpm

COPY Renviron /usr/lib64/R/etc/Renviron.site
COPY Renviron /opt/R/4.5.2/lib/R/etc/Renviron.site

ENV PATH="/opt/R/4.5.2/bin:${PATH}"
