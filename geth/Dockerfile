# https://hub.docker.com/r/ethereum/client-go/
FROM ethereum/client-go:stable

# create working directory and genesis json file
RUN mkdir -p /root/.ethereum/devchain
COPY genesis.json pw /root/.ethereum/devchain/

# create 2 accounts
RUN geth --datadir /root/.ethereum/devchain account new --password /root/.ethereum/devchain/pw && \
    geth --datadir /root/.ethereum/devchain account new --password /root/.ethereum/devchain/pw && \
    echo && \
    echo "*** please backup this output below ***" && \
    echo && \
    cat /root/.ethereum/devchain/keystore/* && \
    echo && \
    echo 

RUN geth --datadir /root/.ethereum/devchain init /root/.ethereum/devchain/genesis.json
