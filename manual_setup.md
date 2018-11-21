# manual set up

## install
mac os

```bash
brew tap ethereum/ethereum
brew install ethereum
```

ubuntu

```bash
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

## setup

create working directory and genesis json file

```bash
mkdir ~/.ethereum/devchain

touch ~/.ethereum/devchain/genesis.json
```

```json
{
  "config": {
    "chainId": 15
  },
  "nonce": "0x0000000000000042",
  "timestamp": "0x0",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "extraData": "",
  "gasLimit": "0x8000000",
  "difficulty": "0x4000",
  "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "coinbase": "0x3333333333333333333333333333333333333333",
  "alloc": {}
}
```

create pw file

```bash
touch ~/.ethereum/devchain/pw
-> please enter the password string in the above file
```

create 2 account (same password)

```bash
geth --datadir ~/.ethereum/devchain account new --password ~/.ethereum/devchain/pw
geth --datadir ~/.ethereum/devchain account new --password ~/.ethereum/devchain/pw
```

confirmation and backup of account information

```bash
cat ~/.ethereum/devchain/keystore/*
```

* initialize block using genesis json file

```bash
geth --datadir ~/.ethereum/devchain init ~/.ethereum/devchain/genesis.json
```

## running

```bash
geth --networkid 15 --nodiscover --datadir ~/.ethereum/devchain --unlock 0,1 --password ~/.ethereum/devchain/pw --port 30303 --rpc --rpcaddr "0.0.0.0" --rpcport 8545 --rpccorsdomain "*" --rpcapi "admin,db,eth,debug,miner,net,shh,txpool,personal,web3"
```
