FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# Update and install required packages
RUN apt-get update && \
    apt-get install -y build-essential autoconf automake libtool pkg-config git wget && \
    apt-get clean

# Install libsodium
RUN wget https://download.libsodium.org/libsodium/releases/libsodium-1.0.18.tar.gz && \
    tar -xf libsodium-1.0.18.tar.gz && \
    cd libsodium-1.0.18 && \
    ./configure && \
    make && \
    make check && \
    make install && \
    cd .. && \
    rm -rf libsodium-1.0.18*   # Clean up downloaded files

# Install Cardano
RUN wget https://github.com/input-output-hk/cardano-node/releases/download/8.1.2/cardano-node-8.1.2-linux.tar.gz && \
    mkdir cardano && \
    tar xf cardano-node-8.1.2-linux.tar.gz -C cardano && \
    mv cardano /usr/local/bin/ && \
    echo 'export PATH="$PATH:/usr/local/bin/cardano"' >> ~/.bashrc && \
    rm cardano-node-8.1.2-linux.tar.gz   # Clean up downloaded file

# Start bash
CMD ["/bin/bash"]

