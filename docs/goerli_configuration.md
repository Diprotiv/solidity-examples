# Etheratom installation
[Etheratom installation](https://github.com/0mkara/etheratom#installation)

# Goerli Testnet Configuration with Etheratom

  1. Install geth & eth
```
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```           
  2. Clone repository:
```
git clone git@github.com:ethereum/go-ethereum.git
cd go-ethereum
```

  3. `make geth` - This will create a geth  executable file in the go-ethereum/build/bin folder that you can move wherever you want to run from.
  4. Creating an account:
```
geth account new
```
  5. Run the following command to initialize the goerli test network:
```
./build/bin/geth --goerli --rpc --rpcaddr=YOUR_LOCAL_IP --rpcapi="eth,web3,personal" --ws --wsaddr=YOUR_LOCAL_IP --wsorigins="*" --wsapi="eth,web3,personal" --keystore YOUR_KEYSTORE_PATH console
```
Default keystore path on Linux: `~/.ethereum/keystore`

Note: If there is any issue with block synchronization, you need to delete the **geth chaindata** and reinitialize the goerli test network.
```
rm -rf /home/USER_NAME/.ethereum/goerli/geth/chaindata
```

6. Connection with Etheratom:

Rpc endpoint: `http://YOUR_LOCAL_IP:8545/`  
Websocket endpoint: `ws://YOUR_LOCAL_IP:8546/`

**** incase of `account unlock with HTTP access is forbidden when unlock an account` this error use the following flag with the command specified in step 5 `--allow-insecure-unlock`. So the full command will be 
```
./build/bin/geth --goerli --rpc --rpcaddr=YOUR_LOCAL_IP --rpcapi="eth,web3,personal" --ws --wsaddr=YOUR_LOCAL_IP --wsorigins="*" --wsapi="eth,web3,personal" --keystore YOUR_KEYSTORE_PATH console --allow-insecure-unlock
```

**** To enable CORS add the folowing flag to your command `--rpccorsdomain "http://localhost:4200"`. So the full command will be
```
./build/bin/geth --goerli --rpc --rpcaddr=YOUR_LOCAL_IP --rpcapi="eth,web3,personal" --ws --wsaddr=YOUR_LOCAL_IP --wsorigins="*" --wsapi="eth,web3,personal" --keystore YOUR_KEYSTORE_PATH console --allow-insecure-unlock --rpccorsdomain "http://localhost:4200"
```
