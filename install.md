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
cabal --version 
~~~

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
