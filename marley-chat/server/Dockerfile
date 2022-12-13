## Base image for marley-chat server image

## Set builder stage
FROM node:16.16.0-buster AS builder

# Set environment/argument variables
ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY
ARG AWS_SESSION_TOKEN
ARG AWS_REGION

# Set environment/argument variables
ENV NPM_VERSION=7.12
ENV AWSCLI_VERSION=1.25.0
# Install system and application dependencies
RUN apt update -y \
    && apt install -y \
    openssh-client \
    git \
    python3 \
    python3-dev \
    python3-venv
RUN  ln -sf /usr/bin/python3 /usr/bin/python
RUN ln -sf /usr/bin/pip3 /usr/bin/pip
#install AWS cli
RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle-$AWSCLI_VERSION.zip" -o "awscli-bundle.zip" \
    && unzip awscli-bundle.zip \
    && ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws \
    && rm -f awscli-bundle.zip
