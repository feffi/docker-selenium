FROM feffi/node-base
MAINTAINER Selenium <feffi@feffi.org>

USER root

#=========
# Firefox
#=========
RUN apt-get update -qqy \
  && apt-get -qqy --no-install-recommends install firefox \
  && rm -rf /var/lib/apt/lists/* \
  && apt-get -y purge firefox
RUN wget --no-verbose -O /tmp/firefox-45.0.2.tar.bz2 https://download-installer.cdn.mozilla.net/pub/firefox/releases/45.0.2/linux-x86_64/en-US/firefox-45.0.2.tar.bz2 \
  && wget --no-verbose -O /tmp/firefox-46.0.1.tar.bz2 https://download-installer.cdn.mozilla.net/pub/firefox/releases/46.0.1/linux-x86_64/en-US/firefox-46.0.1.tar.bz2 \
  && wget --no-verbose -O /tmp/firefox-47.0.1.tar.bz2 https://download-installer.cdn.mozilla.net/pub/firefox/releases/47.0.1/linux-x86_64/en-US/firefox-47.0.1.tar.bz2
RUN mkdir -p /opt/firefox/45.0.2 && tar -C /opt/firefox/45.0.2 --strip-components 1 -xjf /tmp/firefox-45.0.2.tar.bz2 \
  && mkdir -p /opt/firefox/46.0.1 && tar -C /opt/firefox/46.0.1 --strip-components 1 -xjf /tmp/firefox-46.0.1.tar.bz2 \
  && mkdir -p /opt/firefox/47.0.1 && tar -C /opt/firefox/47.0.1 --strip-components 1 -xjf /tmp/firefox-47.0.1.tar.bz2 \
  && rm /tmp/firefox-*.tar.bz2
ENV FIREFOX_VERSION 47.0.1
RUN ln -fs /opt/firefox/${FIREFOX_VERSION}/firefox /usr/bin/firefox

#========================
# Selenium Configuration
#========================
COPY config.json /opt/selenium/config.json

USER seluser
