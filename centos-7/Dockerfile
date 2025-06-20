FROM centos:centos7

# CentOS 7 is EOL so we need to get things from other repos
RUN \
  sed -i 's@^mirrorlist@#mirrorlist@g' /etc/yum.repos.d/*.repo &&\
  sed -i 's@#.*baseurl=http://mirror.centos.org@baseurl=http://vault.centos.org@g' /etc/yum.repos.d/*.repo &&\
  yum update -y &&\
  yum install -y git epel-release curl-devel gawk make patch pkg-config &&\
  yum install -y https://github.com/r-lib/rig/releases/download/latest/r-rig-latest-1.$(arch).rpm && \
  rig add 4.5.1 --without-pak &&\
  if [ $(uname -m) = "x86_64" ]; then yum install -y centos-release-scl; fi &&\
  sed -i 's@^mirrorlist@#mirrorlist@g' /etc/yum.repos.d/*.repo &&\
  sed -i 's@#.*baseurl=http://mirror.centos.org@baseurl=http://vault.centos.org@g' /etc/yum.repos.d/*.repo &&\
  if [ $(uname -m) = "x86_64" ]; then yum install -y devtoolset-8; fi &&\
  yum clean all

ENV PATH="/opt/rh/devtoolset-8/root/usr/bin/:/opt/R/4.5.1/bin:${PATH}"

COPY Renviron /usr/lib64/R/etc/Renviron.site
COPY Renviron /opt/R/4.5.1/lib/R/etc/Renviron.site
