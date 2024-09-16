# Fractal v0.2.1 - Build and Run Instructions

## Steps to Build

Clone the repository and switch to the correct branch:
```bash
git clone --branch v0.2.1 https://github.com/madnadyka/fractal.git
cd fractal
```

### Compile the Node

Run the following commands to compile:
```bash
./autogen.sh
./configure CXXFLAGS="-Wno-unused-result" --with-gui=no --disable-tests --disable-bench"
make clean
make -j8
```

## Running the Node

1. Create a data directory:
    ```bash
    mkdir $HOME/cat/fractal/data
    ```
    
2. Create and edit the configuration file:
    ```bash
    nano $HOME/cat/fractal/data/bitcoin.conf
    ```

### Insert the following into `bitcoin.conf`:

```ini
port=8333

txindex=1
server=1

rpcallowip=0.0.0.0/0
rpcbind=0.0.0.0
rpcport=8332
rpcuser=fbitcoin
rpcpassword=f123
rpcworkqueue=512
rpcthreads=32
rpcservertimeout=60

zmqpubhashblock=tcp://0.0.0.0:8330
zmqpubrawtx=tcp://0.0.0.0:8331

maxconnections=50
```

### Start the Node:

```bash
./src/bitcoind -datadir=$HOME/cat/fractal/data/ -maxtipage=504576000
```

### Check Blockchain Info:

```bash
./src/bitcoin-cli -datadir=$HOME/cat/fractal/data getblockchaininfo
```