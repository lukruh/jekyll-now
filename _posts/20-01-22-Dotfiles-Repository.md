---
layout: post
title: Dotfiles - Sync Configurations with Git
tags: git,sync,config,repository,dotfiles
---

A Git Repository suits very well, for synchronizing your configuration files between different devices or pull them on a fresh installed system. It also provides backups and the possibility to sync only specific files or even specific changes to some of these files. 


## Introduction

Some Applications offer services to sync your settings using their server, but that usually works only for this specific application and you don't have full controll of what and how your configs are stored. Using a version controll system like git instead makes it pretty easy to have custom sets of config files (branches) on different devices and copy, sync or rollback of specific files or folders is as easy as checking out branches or selecting a commit. 
It's common (at least for unix like systems) to store any user specific configuration file in the users home folder as a dotfile (or folder) or inside the `~/.config` directory.
However, config files are usually  text based (`ini`, `json`, `txt`). 
TODO: continue introduction
This approach is used by many developers for themselves or to share their configs with the community.


## Setup the Repository

I found specific introductions how to setup the repository in [this tutorial](https://www.atlassian.com/git/tutorials/dotfiles), which is based on [this post on hacker news](https://news.ycombinator.com/item?id=11070797). The following process is copied from the linked articles.



```shell
git init --bare $HOME/.cfg
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo "alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'" >> $HOME/.bashrc
```

```shell
config status
config add .vimrc
config commit -m "Add vimrc"
config add .bashrc
config commit -m "Add bashrc"
config push
```
