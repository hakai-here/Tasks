FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# Install required dependencies
RUN apt-get update && \
    apt-get install -y build-essential autoconf automake libtool pkg-config git golang

# Clone the Geth repository
RUN git clone https://github.com/ethereum/go-ethereum.git /go/src/github.com/ethereum/go-ethereum

# Set the working directory
WORKDIR /go/src/github.com/ethereum/go-ethereum

# Build Geth
RUN make geth

RUN mv /go/src/github.com/ethereum/go-ethereum/build/bin/geth /usr/local/bin/

# Exposing all necessary ports 
EXPOSE 8545 8546 30303 30303/udp

# Start bash
CMD ["/bin/bash"]