---
layout: post
title: Login to SSH server with your public RSA key
---

Tired of typing your complex password everyday to log in to your host? 
Afraid, someone could guess your password? 
It's pretty easy and timesaving to use your public rsa key to log in.

## Setup RSA Key
This Step is only required if you don't have one yet, or want to create another for a specific connection. 
The users default RSA key is usually stored in `~/.ssh/id_rsa` if this file does not exist create it:
```bash
ssh-keygen -t rsa
```
It's up to you to set a password or not. If you choose one, you'd have to type it in everytime you want to connect.
Than this process may only provide some additional security.

## Add Key to Host
The host system needs to identify you, what it needs is the public part of your key. Either send it from the client device with:
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub user@host
```
or if you are not able to connect with a password, copy the file to your host system manually.
Now you are able to connect to your host with
```bash
ssh user@host
```
wihtout entering a password. If your user name on the local machine the same as on the host system the command becomes even shorter:
```bash
ssh host
```
