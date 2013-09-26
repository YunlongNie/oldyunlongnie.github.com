---
layout: post
title: "Login without password"
date: 2013-07-17 02:12
comments: true
categories: [linux] 
tag: bash
---


say you wanna log into a linux server to do some job. But every time it requires you enter the password, which at least I feel annoying. Here is a way you can generate a key and login without password. 

Suppose we call the local machine A and server as B. Of course, you should have a account for B, say joha@B and password: thissiapassword. 

# How? 
1. first suppose you are on A already and you need to generate a pair of authentication keys. Do not enter any passphrase.
`ssh-keygen -t rsa`

* Defaultly, it will creat a key in ~/.ssh/. 

2. use ssh to creat a folder ~/.ssh as use joha on B. if the folder already exits, it's ok. 
`ssh joha@B mkdir -p .ssh`
enter the password for B. 

3. append A's new public key to joha@B:.ssh/authorized_keys and enter the password for b again. 
`cat .ssh/id_rsa.pub | ssh joha@B 'cat >> .ssh/authorized keys`

4. then you can login B without password
`ssh joha@B`

