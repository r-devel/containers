FROM debian:10

ENV DEBIAN_FRONTEND=noninteractive

RUN sed -i.bak 's@http://deb.debian.org@http://archive.debian.org@g' /etc/apt/sources.list

RUN apt-get -yq update &&\
    apt-get -yq dist-upgrade &&\
    apt-get -yq install lsb-release apt-transport-https ca-certificates locales

RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN if [ $(uname -m) = "x86_64" ]; then echo "deb [trusted=yes] https://cloud.r-project.org/bin/linux/debian $(lsb_release -sc)-cran40/" > /etc/apt/sources.list.d/cran.list; fi && \
    apt-get -yq update &&\
    apt-get -yq dist-upgrade &&\
    apt-get -yq install cloc curl parallel vim wget r-base-dev &&\
    apt-get clean

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

COPY Renviron /etc/R/Renviron.site
