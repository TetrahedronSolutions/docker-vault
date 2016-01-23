FROM alpine:3.2

ENV VAULT_VERSION=0.4.1
ENV VAULT_ADDR=http://localhost:8200

RUN apk --update add curl ca-certificates && \
    curl -Ls https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk > /tmp/glibc-2.21-r2.apk && \
    apk add --allow-untrusted /tmp/glibc-2.21-r2.apk && \
    rm -rf /tmp/glibc-2.21-r2.apk /var/cache/apk/*

ADD https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip /tmp/vault.zip

RUN cd /bin \
    && unzip /tmp/vault.zip \
    && chmod +x /bin/vault \
    && rm /tmp/vault.zip

COPY ./config/ /config/

EXPOSE 8200

CMD vault server -dev
