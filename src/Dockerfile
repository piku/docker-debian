ARG BASE
FROM ${BASE}
ARG ARCH

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
 && apt-get dist-upgrade -y \
 && apt-get install -y \
    build-essential \
    certbot \
    git \
    incron \
    libjpeg-dev \
    libxml2-dev \
    libxslt1-dev \
    libyaml-dev \
    zlib1g-dev \
    maven \
    nginx \
    nodejs \
    openssh-server \
    python-certbot-nginx \
    python-dev \
    python-pip \
    python-virtualenv \
    python3-dev \
    python3-pip \
    python3-click \
    python3-yaml \
    python3-virtualenv \
    uwsgi \
    uwsgi-plugin-asyncio-python3 \
    uwsgi-plugin-gevent-python \
    uwsgi-plugin-python \
    uwsgi-plugin-python3 \
    uwsgi-plugin-tornado-python \
    uwsgi-plugin-lua5.1 \
    uwsgi-plugin-lua5.2 \
    uwsgi-plugin-luajit \
    uwsgi-plugin-jwsgi-openjdk-11 \
    uwsgi-plugin-ring-openjdk-11 \
    locales \
    wget \
 && locale-gen en_US.UTF-8 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /var/tmp/* /tmp/* 

COPY rootfs /

RUN adduser \
    --disabled-password \
    --gecos 'PaaS access' \
    --ingroup www-data \
    piku \
 && su - piku -c "wget https://raw.githubusercontent.com/piku/piku/master/piku.py && python3 ~/piku.py setup" \
 && ln /home/piku/.piku/uwsgi/uwsgi.ini \
       /etc/uwsgi/apps-enabled/piku.ini

ENTRYPOINT [ "/init" ]

ARG VCS_REF
ARG VCS_URL
ARG BUILD_DATE
LABEL org.label-schema.vcs-ref=${VCS_REF} \
      org.label-schema.vcs-url=${VCS_URL} \
      org.label-schema.build-date=${BUILD_DATE}
