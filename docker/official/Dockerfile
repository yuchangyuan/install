FROM alpine:latest

MAINTAINER admin@v2ray.com

COPY v2ray /usr/bin/v2ray/
COPY config.json /etc/v2ray/config.json

RUN apk --update add bash \
    && mkdir /var/log/v2ray/ \
    && chmod +x /usr/bin/v2ray/v2ray \
    && adduser -D -H -s /bin/false v2ray_user v2ray_user \
    && chown -R v2ray_user:v2ray_user /usr/bin/v2ray/ \
    && chown -R v2ray_user:v2ray_user /etc/v2ray/ \
    && chown -R v2ray_user:v2ray_user /var/log/v2ray/ \
    && apk del bash

ENV PATH /usr/bin/v2ray:$PATH

USER v2ray_user

CMD ["v2ray", "-config=/etc/v2ray/config.json"]
