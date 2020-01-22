---
layout: post
title: Dotfiles - Sync Configurations with Git
tags: git,sync,config,repository,dotfiles
---

A Git Repository suits very well, as synchronizer for your configuration files between different devices or fresh installed systems.
Some Applications offer services to sync your settings over their server, but that usually works only for this specific application.
It's common (at least for unix like systems) to store any user specific configuration file in the users home folder as a dotfile (or folder) or inside the `~/.config` directory.
The dot infront of the file/directory name indicates that this file is hidden and therefore these files are often called dot files.
However, config files are usually of a text based file type (`ini`, `json`, `txt`). You probably only want to sync some of them with some of your devices.
You want to be able to change a file on one device, whithout automatically apply this changes everywhere.
This are good reasons to use a git repository to track your configurations, with branches for devices with individual versions of dotfiles.

## Setup the Repository
https://www.atlassian.com/git/tutorials/dotfiles
