FROM realmasterlee/ubuntu:18.04.2

LABEL maintainer="realmasterlee<<785530605@qq.com>"

ENV NGINX_VERSION=1.15.12-1~stretch
ENV NJS_VERSION=1.15.12.0.3.1-1~stretch

RUN mv /etc/apt/sources.list.d/zte_sources.list /etc/apt/sources.list.d/zte_sources.list.bak
RUN mv /etc/apt/sources.list.d/aliyun_sources.list.bak /etc/apt/sources.list.d/aliyun_sources.list

RUN set -x && apt-get update && apt-get install --no-install-recommends --no-install-suggests -y curl gnupg2 ca-certificates lsb-release apt-transport-https ca-certificates

RUN echo "deb http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" | tee /etc/apt/sources.list.d/nginx.list

RUN curl -fsSL https://nginx.org/keys/nginx_signing.key | apt-key add -

RUN apt update && apt install nginx

RUN ln -sf /dev/stdout /var/log/nginx/access.log && ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80

STOPSIGNAL SIGTERM

CMD nginx -g "daemon off;"
