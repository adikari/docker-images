FROM node:14.18.3-alpine

ENV YARN_VERSION 1.19.1

# Install dependencies
RUN apk -v --update add \
        jq \
        python3 \
        cmd:pip3 \
        groff \
        less \
        bash \
        ca-certificates \
        git \
        curl \
        ruby \
        ruby-bundler \
        && pip3 --no-cache-dir install --upgrade awscli

# Remove default yarn
RUN rm /usr/local/bin/yarn /usr/local/bin/yarnpkg

# Install specified version of yarn
RUN apk add --no-cache --virtual .build-deps-yarn gnupg tar \
  && gpg --keyserver keyserver.ubuntu.com --recv-key 908F435E \
  && curl -fsSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz" \
  && curl -fsSLO --compressed "https://yarnpkg.com/downloads/$YARN_VERSION/yarn-v$YARN_VERSION.tar.gz.asc" \
  && gpg --batch --verify yarn-v$YARN_VERSION.tar.gz.asc yarn-v$YARN_VERSION.tar.gz \
  && mkdir -p /opt \
  && tar -xzf yarn-v$YARN_VERSION.tar.gz -C /opt/ \
  && ln -s /opt/yarn-v$YARN_VERSION/bin/yarn /usr/local/bin/yarn \
  && ln -s /opt/yarn-v$YARN_VERSION/bin/yarnpkg /usr/local/bin/yarnpkg \
  && rm yarn-v$YARN_VERSION.tar.gz.asc yarn-v$YARN_VERSION.tar.gz \
  && apk del .build-deps-yarn

# Clean APK cache
RUN rm -rf /var/cache/apk/*
