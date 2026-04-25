FROM ubuntu:resolute

ENV DEBIAN_FRONTEND=noninteractive

RUN apt -yq update &&\
    apt -yq dist-upgrade &&\
    apt -yq install lsb-release apt-transport-https ca-certificates

RUN echo "deb [trusted=yes] https://ppa.launchpadcontent.net/cran/r-4.6/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/cran.list && \
    apt -yq update &&\
    apt -yq dist-upgrade &&\
    apt -yq install language-pack-en-base cloc curl parallel vim wget r-base-dev &&\
    apt clean

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

COPY Renviron /etc/R/Renviron.site
