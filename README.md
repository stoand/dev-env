# Dev Environment with Kakoune and Language Servers

## Setup
```
sudo apt update
sudo apt install ssh git libncursesw5-dev pkg-config tmux -y
ssh-keygen
cat ~/.ssh/id_rsa.pub
# Copy and paste this key to github account settings


git clone git@github.com:stoand/dev-env.git --recurse-submodules -j8 /tmp/dev-env

shopt -s dotglob # Include hidden directories in star
mv /tmp/dev-env/* ~/

# Install Kakoune
(cd ~/.kakoune/src && make -j && PREFIX=$HOME/.local make install)

# Install fzf
~/.fzf/install

# Install kak-lsp
cd /tmp
wget https://github.com/ul/kak-lsp/releases/download/v7.0.0/kak-lsp-v7.0.0-x86_64-unknown-linux-musl.tar.gz
tar xzvf kak-lsp-v7.0.0-x86_64-unknown-linux-musl.tar.gz
mv kak-lsp ~/.local/bin/

# Start tmux and kakoune
source ~/.bashrc
tm

# To start using languages you have to install servers
# https://github.com/ul/kak-lsp/wiki/How-to-install-servers

# Ocaml lsp (only supports 4.08.0 and under)
opam pin add ocaml-lsp-server https://github.com/ocaml/ocaml-lsp.git

# To get the correct theme in Konsole
# Right click -> Edit Current Profile -> Appearance -> KakouneBase16
```
