# Configuration
## Oneshell means all lines in a recipe run in the same shell
.ONESHELL:


# Variables
ROOT_UNIVERSE := $(abspath $(dir $(lastword $(MAKEFILE_LIST)))/../../../)


# Shortcuts
## Linux-specific
install__linux: install-fzf__linux install-tpm install-starship__linux install-vundle install-zoxide__linux install-zsh-autosuggestions__linux
link__linux: link-git link-tmux link-starship link-vim link-zsh__linux
upgrade__linux: upgrade-fzf__linux upgrade-tpm upgrade-vundle upgrade-zsh-autosuggestions__linux


# Command section
## Non-specific
### Deactivating the prompt modifier of conda (useful only when starship is applied)
command-conda-mute:
	-conda config --set changeps1 false

### Deactivating conda on startup
command-conda-not-on-startup:
	-conda config --set auto_activate_base false

### Initiating git lfs for a user account
command-git-lfs-init-account:
	-git lfs install

### Installing tpm plugins specified in tmux conf
command-tpm-install-plugins:
	-$(ROOT_UNIVERSE)/bin/tmux/plugins/tpm/bin/install_plugins

### Installing vundle plugins specified in vim conf
command-vundle-install-plugins:
	-vim +PluginInstall +qall

## Linux-specific
### Setup zsh as default shell
command-os-setup-zsh__linux:
	-chsh -s $(which zsh)


# Installing section
## Non-specific
install-tpm:
	-git clone https://github.com/tmux-plugins/tpm $(ROOT_UNIVERSE)/bin/tmux/plugins/tpm

install-vundle:
	-git clone https://github.com/VundleVim/Vundle.vim.git $(ROOT_UNIVERSE)/bin/vim/bundle/Vundle.viml

## Linux-specific
install-conda__linux:
	-mkdir -p $(ROOT_UNIVERSE)/bin/miniconda3 && wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O $(ROOT_UNIVERSE)/bin/miniconda3/miniconda.sh && bash $(ROOT_UNIVERSE)/bin/miniconda3/miniconda.sh -b -u -p $(ROOT_UNIVERSE)/bin/miniconda3 && rm -rf $(ROOT_UNIVERSE)/bin/miniconda3/miniconda.sh

install-fzf__linux:
	-git clone --depth 1 https://github.com/junegunn/fzf.git $(ROOT_UNIVERSE)/bin/fzf/ && $(ROOT_UNIVERSE)/bin/fzf/install --key-bindings --completion --no-update-rc

install-starship__linux:
	-curl -sS https://starship.rs/install.sh | sh

install-zoxide__linux:
	-curl -sSfL https://raw.githubusercontent.com/ajeetdsouza/zoxide/main/install.sh | sh

install-zsh-autosuggestions__linux:
	-git clone https://github.com/zsh-users/zsh-autosuggestions $(ROOT_UNIVERSE)/bin/zsh-autosuggestions/


# Upgrading section
## Non-specific
upgrade-tpm:
	-git -C $(ROOT_UNIVERSE)/bin/tmux/plugins/tpm pull

upgrade-vundle:
	-git -C $(ROOT_UNIVERSE)/bin/vim/bundle/Vundle.vim pull && vim +PluginInstall +qall

## Linux-specific
upgrade-fzf__linux:
	-git -C $(ROOT_UNIVERSE)/bin/fzf pull && $(ROOT_UNIVERSE)/bin/fzf/install --key-bindings --completion --no-update-rc

upgrade-zsh-autosuggestions__linux:
	-git -C $(ROOT_UNIVERSE)/bin/zsh-autosuggestions pull


# Link section
## Non-specific
link-bash:
	-ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/all/bash/{.bash_profile,.inputrc} ~

link-git:
	-ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/all/git/.gitconfig ~

link-tmux:
	-ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/all/tmux/.tmux.conf ~

link-starship:
	-mkdir -p ~/.config/ && ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/all/starship/starship.toml ~/.config/

link-vim:
	-ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/all/vim/.vimrc ~

## Linux-specific
link-zsh__linux:
	-ln -sf $(ROOT_UNIVERSE)/files/server/client/auto/linux/zsh/.zshrc ~
