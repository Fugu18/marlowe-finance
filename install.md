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

A N N

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
