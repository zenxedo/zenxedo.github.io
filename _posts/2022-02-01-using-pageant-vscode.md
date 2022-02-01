---
title: "Using Pageant with VS Code Remote Development"
date: 2019-04-18T15:34:30-04:00
categories:
  - blog
tags:
  - Jekyll
  - update
---
## Using Pageant with VS Code Remote Development

Copied from
'link https://rfdonnelly.github.io/posts/vscode-remote-with-pageant/'


This article documents using Pageant to manage SSH keys for VS Code Remote.

## Assumptions
VS Code and the VS Code Remote Development extension is installed

PuTTY Pageant is being used to manage SSH keys

The remote host has a corresponding public key

## Introduction
VS Code Remote Development doesn’t support Pageant out of the box.⁠[1] More specifically, VS Code Remote Development uses the Windows 10 native OpenSSH client and the OpenSSH client doesn’t support Pageant. A bridge is needed to make Pageant available to the OpenSSH client.

This is where wsl-ssh-pageant comes in. wsl-ssh-pageant can make Pageant available to WSL or the Windows OpenSSH client. We are going to use it to make Pageant available to the Windows OpenSSH client.

## Install wsl-ssh-pageant
Download wsl-ssh-pageant-amd64-gui.exe from the latest release of wsl-ssh-pageant⁠[2]

## Note
The -gui version doesn’t actually provide a GUI but rather it doesn’t open a terminal while the non-gui version does.
Setup wsl-ssh-pageant
Open the startup directory by pressing ⊞Win+R and typing shell:startup↵

Create a .bat file with the following content⁠[3]

```
@ECHO OFF
SETX SSH_AUTH_SOCK \\.\pipe\ssh-pageant
START /B "" "C:\SSH\wsl-ssh-pageant-amd64-gui.exe" --systray --winssh ssh-pageant
Run the .bat file
```

## Use VS Code Remote Development
Open VS Code and connect to a remote host. You should no longer be prompted for a password.

## My notes