FROM node:16-alpine

ENV AWSCLI_VERSION=1.25.0

# Install system dependencies and add node_modules binaries to PATH
RUN apk add --update \
    git \
    curl \
    openssh-client \
    python3 \
    python3-dev \
    && ln -sf /usr/bin/python3 /usr/bin/python \
    && ln -sf /usr/bin/pip3 /usr/bin/pip \
    && apk --no-cache add unzip \
    && rm -rf /var/cache/apk/*  \
    && PATH=$PATH:/app/node_modules/.bin

#install AWS cli
RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle-$AWSCLI_VERSION.zip" -o "awscli-bundle.zip" \
    && unzip -q awscli-bundle.zip \
    && ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws \
    && rm -f awscli-bundle.zip
