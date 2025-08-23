FROM opensuse/leap:15.6

RUN zypper install -y R-devel gcc gcc-c++ gcc-fortran make patch gzip tar libcurl-devel zlib-devel

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

COPY Renviron /etc/R/Renviron.site
