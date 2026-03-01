FROM ubuntu:noble

ENV DEBIAN_FRONTEND=noninteractive

RUN apt -yq update &&\
    apt -yq dist-upgrade &&\
    apt -yq install language-pack-en-base cloc curl parallel vim wget lsb-release apt-transport-https ca-certificates

RUN curl -o r-devel.deb -LSsf "https://cdn.posit.co/r/ubuntu-2404/pkgs/r-devel_1_$(dpkg --print-architecture).deb" &&\
    apt install --reinstall -y -o=Dpkg::Use-Pty=0 -o=Apt::Cmd::Disable-Script-Warning=1 ./r-devel.deb && rm r-devel.deb &&\
    sed -i.bak 's|-g ||g' /opt/R/devel/lib/R/etc/Makeconf  &&\
    apt clean

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

ENV PATH="/opt/R/devel/bin:${PATH}"

COPY Renviron /opt/R/devel/lib/R/etc/Renviron.site
