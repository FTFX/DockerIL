FROM alpine:latest
ENV VERSION=1.43.2
WORKDIR /opt/

RUN set -x \
    && apk add --no-cache  --virtual .deps \
        cmake \
        pkgconfig \
        gcc \
        make \
        g++ \
        python \
        npm \
        libx11-dev \
        libxkbfile-dev \
        libsecret-dev \
    && apk add --no-cache yarn \
    && wget https://github.com/microsoft/vscode/archive/${VERSION}.tar.gz \
    && tar -xzf ${VERSION}.tar.gz \
    && mv vscode-${VERSION} vscode \
    && cd vscode \
    && yarn \
    && yarn compile \
    && apk del .deps

WORKDIR /opt/vscode

ENTRYPOINT [ "yarn", "web" ]
