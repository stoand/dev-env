# Dev Environment with Kakoune and Language Servers

## Setup
```
sudo apt update
sudo apt install ssh git libncursesw5-dev pkg-config tmux xsel ripgrep -y
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
wget https://github.com/ul/kak-lsp/releases/download/v10.0.0/kak-lsp-v10.0.0-x86_64-unknown-linux-musl.tar.gz
tar xzvf kak-lsp-v10.0.0-x86_64-unknown-linux-musl.tar.gz
mv kak-lsp ~/.local/bin/

# Start tmux and kakoune
source ~/.bashrc
tm

# To start using languages you have to install servers
# https://github.com/ul/kak-lsp/wiki/How-to-install-servers

# Java lsp
mkdir ~/.local/share/java-lsp/
cd ~/.local/share/java-lsp/
wget https://download.eclipse.org/jdtls/snapshots/jdt-language-server-1.6.0-202111171744.tar.gz
tar -xf jdt-language-server-1.6.0-202111171744.tar.gz

# Ocaml lsp (only supports 4.08.0 and under)
opam pin add ocaml-lsp-server https://github.com/ocaml/ocaml-lsp.git
opam install ocamlformat
# Do not forget to create `.ocamlformat` in project dir

# Haskell lsp

* Install stack
* `wget` then `tar -xf` latest `.tar.gz` Linux (release)[https://github.com/haskell/haskell-language-server/releases] 
* cp all haskell* files to ~/.local/bin

# To get the correct theme in Konsole
# Right click -> Edit Current Profile -> Appearance -> KakouneBase16
```
