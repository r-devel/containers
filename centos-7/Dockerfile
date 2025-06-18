FROM centos:centos7

# CentOS 7 is EOL so we need to get things from other repos
RUN if [ $(uname -m) = "x86_64" ]; then \
  DOWNLOAD="https://cdn.rstudio.com/r/centos-7/pkgs/R-4.5.1-1-1.x86_64.rpm"; \
  else \
  DOWNLOAD="https://github.com/r-hub/R/releases/download/v4.5.1/r-rstudio-centos-7-4.5.1-1-1.aarch64.rpm"; \
  fi &&\
  sed -i 's@^mirrorlist@#mirrorlist@g' /etc/yum.repos.d/*.repo &&\
  sed -i 's@#.*baseurl=http://mirror.centos.org@baseurl=http://vault.centos.org@g' /etc/yum.repos.d/*.repo &&\
  yum update -y &&\
  yum install -y git epel-release &&\
  curl -fsSL "$DOWNLOAD" -o R-base.rpm &&\
  yum install -y R-base.rpm &&\
  rm -f R-base.rpm &&\
  yum clean all


# This is not available for ARM64 anymore
RUN if [ $(uname -m) = "x86_64" ]; then \
  yum install -y centos-release-scl &&\
  sed -i 's@^mirrorlist@#mirrorlist@g' /etc/yum.repos.d/*.repo &&\
  sed -i 's@#.*baseurl=http://mirror.centos.org@baseurl=http://vault.centos.org@g' /etc/yum.repos.d/*.repo &&\
  yum install -y devtoolset-8; \
  fi

ENV PATH="/opt/rh/devtoolset-8/root/usr/bin/:/opt/R/4.5.1/bin:${PATH}"
