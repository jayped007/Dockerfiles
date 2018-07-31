FROM debian

LABEL maintainer=@jayped007

# DEBIAN_FRONTEND ==> interaction with container, interactive?
ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies -- wget command, etc
RUN apt-get update --fix-missing && \
   apt-get install -y \
      wget bzip2 ca-certificates libglib2.0-0 libxext6 libsm6 libxrender1
