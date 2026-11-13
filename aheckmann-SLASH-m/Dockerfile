
FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive
ENV PATH="/root/.local/bin:${PATH}"

# Install dependencies
RUN apt-get update && apt-get install -y \
    bash \
    curl \
    ca-certificates \
    tar \
    xz-utils \
    libcurl4 \
    libssl3 \
    && rm -rf /var/lib/apt/lists/*

# Install MongoDB version manager
RUN curl -fsSL \
    https://raw.githubusercontent.com/aheckmann/m/master/bin/m \
    -o /usr/local/bin/m \
    && chmod +x /usr/local/bin/m

# Download and activate MongoDB 8.0
RUN yes | m 8.0

# Verify MongoDB installation
RUN mongod --version \
    && command -v mongod

# Create MongoDB data directory
RUN mkdir -p /data/db

VOLUME ["/data/db"]

EXPOSE 27017

CMD ["mongod", "--bind_ip_all", "--dbpath", "/data/db"]
