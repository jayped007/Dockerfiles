FROM debian

LABEL maintainer=@jayped007

# DEBIAN_FRONTEND ==> interaction with container, interactive?
ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies -- wget command, etc
RUN apt-get update --fix-missing && \
   apt-get install -y \
      wget bzip2 ca-certificates libglib2.0-0 libxext6 libsm6 libxrender1

# Install miniconda
RUN \
    echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet \
        https://repo.continuum.io/miniconda/Miniconda3-4.3.11-Linux-x86_64.sh \
        -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh

# Install tini -- reap zombies, exit at appropriate time
RUN \
    apt-get install -y curl grep sed dpkg && \
    TINI_VERSION=`curl https://github.com/krallin/tini/releases/latest | grep -o "/v.*\"" | sed 's:^..\(.*\).$:\1:'` && \
    curl -L "https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini_${TINI_VERSION}.deb" > tini.deb && \
    dpkg -i tini.deb && \
    rm tini.deb && \
    apt-get clean

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

ENTRYPOINT [ "/usr/bin/tini", "--" ]

