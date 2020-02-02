---
state: draft
tags: [git, config, firefox, thunderbird, profile, settingis, sync, import, export]
date: 2020-01-15
---



# Export/Import Thunderbird or Firefox Profiles



## git config notes

To keep parts of your profiles in sync with the git based dotfiles concept, rename the profile folder and apply the profile.ini. Pass the files via `config add .thunderbird/xxxx.profile/specific/file/or/folder` to the dotfile repo commit and push it. Pull on the same branch (remote machine) and when the remote machine has an own branch, checkout specific files from master (or whereever the files where added).

When most of the profile should be in tracked by git, also .gitignore can be used to exclude specific file and add the folder (not tested).

