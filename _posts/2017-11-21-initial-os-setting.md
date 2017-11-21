---
layout: post
title:  "Initial OS Setting"
date:   2017-11-21 11:00:00 +0900
categories: howto
---

# Contents
1. [Initial macOS Setting](#initial-macos-setting)
2. [Initial Ubuntu Setting](#initial-ubuntu-setting)

# Initial macOS Setting

## All in one script

```
xcode-select --install
git clone https://github.com/trilliwon/config.git && ./config/install.sh
```
## LocalHostName

```
sudo scutil --set LocalHostName <NEW NAME>
```

## Package Manager

- [Homebrew](https://brew.sh)
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Terminal

- install Xcode
- install git
- install [Bash-it](https://github.com/Bash-it/bash-it)
- install gcc g++ vim cmake

## Vim

- [.vimrc](https://github.com/trilliwon/config/blob/master/.vimrc)
- [.inputrc](https://github.com/trilliwon/config/blob/master/.inputrc)
- [vundle : plug-in manager for Vim](https://github.com/VundleVim/Vundle.vim)
  - `git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it`

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

:PluginInstall # vim
vim +PluginInstall +qall # command line
```

## Applications

- [Alfred3](https://www.alfredapp.com)
- [Atom](https://atom.io)
- [VirtualBox](https://www.virtualbox.org)
- [Chrome](https://www.google.com/chrome/)
- Xcode
- [Dropbox](https://www.dropbox.com)
 - `https://www.dropbox.com/download?os=mac`

---

# Initial Ubuntu Setting

## All in one script
```
sudo apt-get install git # for ubuntu
git clone https://github.com/trilliwon/config.git && ./config/install.sh
```
## HostName
```
sudo hostname <NEW NAME>
```

## git credential config
```
git config --global credential.helper 'store --file ~/.git-credentials'
```

## cscope Installation

- `sudo apt-get install cscope`
