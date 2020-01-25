FROM debian:bullseye-slim

# Install collectd and dependencies for fritzcollectd.
RUN \
    apt-get update -qq \
 && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -qq \
        collectd \
        libpython3.7 \
        python3-setuptools \
        python3-wheel \
        python3-pip \
        python3-requests \
        python3-lxml \
 && apt-get clean \
 && rm -f /var/lib/apt/lists/deb* /var/lib/apt/lists/sec*

RUN pip3 install --no-cache-dir --progress-bar off fritzcollectd

# Copy entrypoint script.
COPY entrypoint.sh /
RUN chmod 755 /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
