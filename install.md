## Creating and Funding Wallets

**1. Lace Wallet**

One-stop wallet integrating all tokens, NFTs and dApps from Cardano founding entity Input Output Global. The popular open source, community-built NAMI wallet is now part of Lace.

[Lace Browser Plugin](https://chromewebstore.google.com/detail/lace/gafhhkghbfjjkeiendhlofajokpaflmk?hl=en)

**2. Yoroi Wallet**

Built by another Cardano founding entity, Emurgo, the legacy Yoroi Wallet is a self custodial open-source light wallet built in the open for the Cardano ecosystem. The level of transparency enhances its security.

[Yoroi Browser Plugin](https://chromewebstore.google.com/detail/yoroi/ffnbelfdoeiohenkjibnmadjiehjhajb)

**3. Eternl Wallet**

The Cardano light wallet. Built by Tastenkunst GmbH, one of the major Cardano wallets implementing features requested by the Cardano community.

[Eternl Browser Plugin](https://chromewebstore.google.com/detail/eternl/kmhcihpebfmpgmihbkipmjlmmioameka)

---

Fund your wallets with test-ADA (no value IRL!!!) to safely and cheaply test your smart contracts outside sim, in close-to-production blockchain environments.

[Cardano Testnets Faucet](https://docs.cardano.org/cardano-testnets/tools/faucet)

---


## User, Node and CLI Setup

### Creating a dedicated Cardano User

```
sudo adduser cardano
sudo usermod -aG sudo cardano
sudo su – cardano
```

### Preparing node installation
~~~
sudo apt-get update -y
sudo apt-get upgrade -y
~~~

~~~
sudo apt-get install automake build-essential pkg-config libffi-dev libgmp-dev libssl-dev libsystemd-dev zlib1g-dev make g++ tmux git jq wget libncurses-dev libtool autoconf curl python3 htop nload -y
export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"
~~~

~~~
curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh
~~~

~~~
source /home/cardano/.ghcup/env
~~~

~~~
ghcup install cabal 3.8.1.0
ghcup set cabal 3.8.1.0
cabal update
ghcup install ghc 8.10.7
~~~


### Node installation

Updating to the desired version of Cardano Node

```
CARDANO_NODE_VERSION='XX.Y.Z'
IOHKNIX_VERSION=$(curl https://raw.githubusercontent.com/IntersectMBO/cardano-node/$CARDANO_NODE_VERSION/flake.lock | jq -r '.nodes.iohkNix.locked.rev')
echo "iohk-nix version: $IOHKNIX_VERSION"
```

We need to install several packages required for the node to run. We will set up a source folder 'src' for this purpose.

```
mkdir src
cd src
```

Sodium or Libsodium is a powerful cryptography library that is a portable, cross-compilable, installable, and packageable fork of NaCl, a famous cryptographic tool designed by [Prof. D.J. Bernstein](https://en.wikipedia.org/wiki/Daniel_J._Bernstein).

```
SODIUM_VERSION=$(curl https://raw.githubusercontent.com/input-output-hk/iohk-nix/$IOHKNIX_VERSION/flake.lock | jq -r '.nodes.sodium.original.rev')
echo "Using sodium version: $SODIUM_VERSION"
```

After getting the version tag, we can proceed and install sodium.

```
: ${SODIUM_VERSION:='dbb48cc'}
git clone https://github.com/intersectmbo/libsodium
cd libsodium
git checkout $SODIUM_VERSION
./autogen.sh
./configure
make
make check
sudo make install
```

Finally, we add the path to our .bashrc file:

```
export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"
export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"
source ~/.bashrc
```

We will also need to install Secp256k1 for the Cardano Node, the software providing logic for the elliptic curve used for UTxO to implement its public key cryptography (from Bitcoin). Again, we begin by obtaining the version...

```
SECP256K1_VERSION=$(curl https://raw.githubusercontent.com/input-output-hk/iohk-nix/$IOHKNIX_VERSION/flake.lock | jq -r '.nodes.secp256k1.original.ref')
echo "Using secp256k1 version: ${SECP256K1_VERSION}"
```

...and then installing it (also in our `src` folder):

```
: ${SECP256K1_VERSION:='v0.3.2'}
git clone --depth 1 --branch ${SECP256K1_VERSION} https://github.com/bitcoin-core/secp256k1
cd secp256k1
./autogen.sh
./configure --enable-module-schnorrsig --enable-experimental
make
make check
sudo make install
```

```
BLST_VERSION=$(curl https://raw.githubusercontent.com/input-output-hk/iohk-nix/master/flake.lock | jq -r '.nodes.blst.original.ref')
echo "Using blst version: ${BLST_VERSION}"
```

```
: ${BLST_VERSION:='v0.3.11'}
git clone --depth 1 --branch ${BLST_VERSION} https://github.com/supranational/blst
cd blst
./build.sh
cat > libblst.pc << EOF
prefix=/usr/local
exec_prefix=\${prefix}
libdir=\${exec_prefix}/lib
includedir=\${prefix}/include

Name: libblst
Description: Multilingual BLS12-381 signature library
URL: https://github.com/supranational/blst
Version: ${BLST_VERSION#v}
Cflags: -I\${includedir}
Libs: -L\${libdir} -lblst
EOF
sudo cp libblst.pc /usr/local/lib/pkgconfig/
sudo cp bindings/blst_aux.h bindings/blst.h bindings/blst.hpp  /usr/local/include/
sudo cp libblst.a /usr/local/lib
sudo chmod u=rw,go=r /usr/local/{lib/{libblst.a,pkgconfig/libblst.pc},include/{blst.{h,hpp},blst_aux.h}}
```

After these dependencies have been installed, we can restart our terminal and proceed to install the Cardano node. We do not need to decide yet which network we want to run, and can later set up mainnet, Preprod or Preview testnets in separate folders.


### Installing Marlowe CLI

~~~
git clone https://github.com/input-output-hk/marlowe-cardano.git
cd marlowe-cardano
cabal install exe:marlowe-cli
~~~

*References*

[Mainnet Node](https://book.play.dev.cardano.org/env-mainnet.html)

~~~
marlowe-cli : a command-line tool for Marlowe contracts

Usage: marlowe-cli [--version] 
                   (COMMAND | COMMAND | [--alonzo-era] (COMMAND | COMMAND) | 
                     --babbage-era (COMMAND | COMMAND))

  Utilities for Marlowe.

Available options:
  -h,--help                Show this help text
  --version                Show version.
  --alonzo-era             Read and write Alonzo transactions
  --babbage-era            Read and write Babbage transactions
  --conway-era             Read and write Conway transactions

High-level commands:
  run                      Run a contract.
  template                 Create a contract from a template.
  test                     Test contracts.

Low-level commands:
  contract                 Export contract address, validator, datum, or
                           redeemer.
  input                    Create inputs to a contract.
  role                     Export role address, validator, datum, or redeemer.
  transaction              Create and submit transactions.
  util                     Miscellaneous utilities.
~~~
