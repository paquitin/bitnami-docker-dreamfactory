FROM bitnami/minideb-extras:stretch-r153
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages libbz2-1.0 libc6 libcomerr2 libcurl3 libexpat1 libffi6 libfreetype6 libgcc1 libgcrypt20 libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed4 libicu57 libidn11 libidn2-0 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libmcrypt4 libncurses5 libnettle6 libnghttp2-14 libp11-kit0 libpcap0.8 libpcre3 libpng16-16 libpq5 libpsl5 libreadline7 librtmp1 libsasl2-2 libsqlite3-0 libssh2-1 libssl1.0.2 libssl1.1 libstdc++6 libsybdb5 libtasn1-6 libtidy5 libtinfo5 libunistring0 libuv1 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg unpack apache-2.4.35-0 --checksum 1e352e2185137fcad60bb6fdf2961368f59a35e2c2cab4ee94c77152f1c37299
RUN bitnami-pkg install redis-client-4.0.11-0 --checksum 8ebad261d5980dcf15659b306f7db7878363c26513ca49381e97427e52ffcc0b
RUN bitnami-pkg unpack php-7.0.32-1 --checksum ba35c87fa72b1333c036491734e039bac53f5726c1e2458ce8126473240c3cc8
RUN bitnami-pkg install mysql-client-10.2.18-0 --checksum 2ae3b6c2dc5f69815a2387776624bcc46cff197ac7cb78f8009e535f3662971a
RUN bitnami-pkg install mongodb-client-3.6.5-0 --checksum daedf94d3e810241da609b997537cc0031663ad2d18d3b1c1457a5d60fcf5443
RUN bitnami-pkg install libphp-7.0.32-2 --checksum 03bb40ebb66af0ce2b1dc5cd9aeded75811e695e184e67b74f45b405a86af2a2
RUN bitnami-pkg unpack dreamfactory-2.12.0-0 --checksum 77aebf82a50fe7fed065bb0025e12d75bf2e5549ed21b5e61313ea04f4480df7

COPY rootfs /
ENV APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="dreamfactory" \
    BITNAMI_IMAGE_VERSION="2.12.0-debian-9-r75" \
    MARIADB_HOST="mariadb" \
    MARIADB_PASSWORD="" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_USER="root" \
    MONGODB_HOST="mongodb" \
    MONGODB_PASSWORD="" \
    MONGODB_PORT_NUMBER="27017" \
    MONGODB_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/redis/bin:/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/mysql/bin:/opt/bitnami/mongodb/bin:$PATH" \
    REDIS_HOST="redis" \
    REDIS_PASSWORD="" \
    REDIS_PORT_NUMBER="6379" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="" \
    SMTP_USER=""

EXPOSE 80 443

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "apache" ]
