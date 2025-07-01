FROM debian:trixie

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -yq update &&\
    apt-get -yq dist-upgrade &&\
    apt-get -yq install lsb-release apt-transport-https ca-certificates locales

RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN apt-get -yq update &&\
    apt-get -yq dist-upgrade &&\
    apt-get -yq install cloc curl parallel vim wget r-base-dev &&\
    apt-get clean

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

COPY Renviron /etc/R/Renviron.site
