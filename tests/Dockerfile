FROM debian:11.6

ENV DEBIAN_FRONTEND noninteractive

RUN apt update \
    && apt install --yes ca-certificates apt-transport-https lsb-release wget curl \
    && curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg \ 
    && sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list' \
    && apt update \
    && apt install --yes --no-install-recommends \
    apache2 \
    php8.1 \
    php8.1-mysql \
    php8.1-ldap \
    php8.1-xmlrpc \
    php8.1-imap \
    php8.1-curl \
    php8.1-gd \
    php8.1-mbstring \
    php8.1-xml \
    php-cas \
    php8.1-intl \
    php8.1-zip \
    php8.1-bz2 \
    php8.1-redis \
    cron \
    jq \
    libldap-2.4-2 \
    libldap-common \
    libsasl2-2 \
    libsasl2-modules \
    libsasl2-modules-db \
    && rm -rf /var/lib/apt/lists/*

COPY tests/start.sh /opt/
RUN chmod +x /opt/start.sh
ENTRYPOINT ["/opt/start.sh"]

EXPOSE 80
