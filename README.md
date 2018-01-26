Quick Start
-----------

1. Create a `bitconnectd-data` volume to persist the bitconnectd blockchain data, should exit immediately.  The `bitconnectd-data` container will store the blockchain when the node container is recreated (software upgrade, reboot, etc):

        docker volume create --name=bitconnectd-data
        docker run -v bitconnectd-data:/root/.bitconnect --name=bitconnectd-node -d \
            -p 0000:0000 \
            -p 127.0.0.1:0000:0000 \
            xxx/bitconnectdd

2. Verify that the container is running and bitconnectd node is downloading the blockchain

        $ docker ps
        CONTAINER ID        IMAGE                         COMMAND             CREATED             STATUS              PORTS                                              NAMES
        d0e1076b2dca        xxx/bitconnectd:latest     "bitconnectd"       2 seconds ago       Up 1 seconds        127.0.0.1:8332->8332/tcp, 0.0.0.0:8333->8333/tcp   bitcoind-node

3. You can then access the daemon's output thanks to the [docker logs command]( https://docs.docker.com/reference/commandline/cli/#logs)

        docker logs -f bitconnectd-node
