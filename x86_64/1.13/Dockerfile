FROM ubuntu:16.04

RUN apt-get update && \
  echo "ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true" | debconf-set-selections && \
  apt-get install -y software-properties-common \
  msttcorefonts \
  fonts-liberation \
  fonts-thai-tlwg \
  fonts-indic \
  fontconfig \
  libappindicator3-1 \
  locales \
  libfontconfig1 \
  unzip \
  libasound2 \
  libnspr4 \
  libnss3 \
  libxss1 \
  xdg-utils \
  build-essential python-dev python-pip wget
  
RUN wget https://mupdf.com/downloads/archive/mupdf-1.13.0-source.tar.gz -O /mupdf-source.tgz && \
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -O /google-chrome-stable_current_amd64.deb &&\
    wget https://chromedriver.storage.googleapis.com/74.0.3729.6/chromedriver_linux64.zip -O /chromedriver_linux64.zip &&\
    dpkg -i google-chrome-stable_current_amd64.deb &&\
    rm /google-chrome-stable_current_amd64.deb
    
RUN unzip /chromedriver_linux64.zip && mv /chromedriver /usr/bin/ && rm /chromedriver_linux64.zip
RUN cd / && tar -zxf mupdf-source.tgz && rm mupdf-source.tgz
RUN cd /mupdf-1.13.0-source && make HAVE_X11=no HAVE_GLUT=no prefix=/usr install
RUN rm -rf /mupdf-1.13.0-source /var/lib/apt/lists/*
