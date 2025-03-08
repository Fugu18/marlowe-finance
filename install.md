## Creating and Funding Wallets

One-stop wallet integrating all tokens, NFTs and dApps from Cardano founding entity Input Output Global. The popular open source, community-built NAMI wallet is now part of Lace.

[Lace Browser Plugin](https://chromewebstore.google.com/detail/lace/gafhhkghbfjjkeiendhlofajokpaflmk?hl=en)


Built by another Cardano founding entity, Emurgo, the legacy Yoroi Wallet is a self custodial open-source light wallet built in the open for the Cardano ecosystem. The level of transparency enhances its security.

[Yoroi Browser Plugin](https://chromewebstore.google.com/detail/yoroi/ffnbelfdoeiohenkjibnmadjiehjhajb)


The Cardano light wallet. Built by Tastenkunst GmbH, one of the major Cardano wallets implementing features requested by the Cardano community.

[Eternl Browser Plugin](https://chromewebstore.google.com/detail/eternl/kmhcihpebfmpgmihbkipmjlmmioameka)


Fund your wallets with test-ADA (no value IRL!!!) to safely and cheaply test your smart contracts outside sim, in close-to-production blockchain environments.

[Cardano Testnets Faucet](https://docs.cardano.org/cardano-testnets/tools/faucet)


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

Updating to the desired version of Cardano Node
```
CARDANO_NODE_VERSION='XX.Y.Z'
IOHKNIX_VERSION=$(curl https://raw.githubusercontent.com/IntersectMBO/cardano-node/$CARDANO_NODE_VERSION/flake.lock | jq -r '.nodes.iohkNix.locked.rev')
echo "iohk-nix version: $IOHKNIX_VERSION"
```

We need to install several packages required for the node to run:

```
SODIUM_VERSION=$(curl https://raw.githubusercontent.com/input-output-hk/iohk-nix/$IOHKNIX_VERSION/flake.lock | jq -r '.nodes.sodium.original.rev')
echo "Using sodium version: $SODIUM_VERSION"
```

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
