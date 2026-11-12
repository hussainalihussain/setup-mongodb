
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

# Install MongoDB version manager (m)
RUN curl -fsSL \
    https://raw.githubusercontent.com/aheckmann/m/master/bin/m \
    -o /usr/local/bin/m \
    && chmod +x /usr/local/bin/m

# Install MongoDB 8.0
RUN m 8.0

# Create MongoDB data directory
RUN mkdir -p /data/db

VOLUME ["/data/db"]

EXPOSE 27017

CMD ["mongod", "--bind_ip_all", "--dbpath", "/data/db"]
