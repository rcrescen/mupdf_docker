FROM ubuntu:20.04

RUN ln -fs /usr/share/zoneinfo/America/Mexico_City /etc/localtime && \
  apt-get update && \
  DEBIAN_FRONTEND=noninteractive  apt-get install -y software-properties-common \
  unzip build-essential python3 python3-dev python3-pip wget
  
RUN wget https://mupdf.com/downloads/archive/mupdf-1.19.1-source.tar.gz -O /mupdf-source.tgz && \
    cd / && tar -zxf mupdf-source.tgz && rm mupdf-source.tgz && \
    cd /mupdf-1.19.1-source && make HAVE_X11=no HAVE_GLUT=no prefix=/usr install  && \
    rm -rf /mupdf-1.19.1-source /var/lib/apt/lists/*
