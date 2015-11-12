---
layout: post
title: "Improve your ssh-foo: Quick way to bridge multiple ssh-servers"
date: 2013-07-29 18:10
comments: true
categories: [ssh, How To, Linux]
---

While I work from my trustworthy Macbook Pro, everything in this tutorial should translate easily to any Unix-variant OS. 

This document explains how to access a ssh-enabled server by using another server as **a bridge**. This may be relevant if you must access server **S2**, say, in order to to carry out some calculations, but **S2** is only connected to a university network **S1**. From your home computer you would have to first ssh into **S1** and then ssh into **S2**. This quickly becomes messy, when you wish to do anything remotely complicated like transferring files between different machines.

In the end of this tutorial you should be able to simply write `ssh S2`. And then end up immediately in **S2**. Similarly you can use any ssh-based technology like the terminal-based `scp S2:file .`, or drag-and-drop based solutions like MacFusion without ever thinking about the complicated two stage ssh-connection.

## Prerequisites

The ssh program must of course be installed on your home computer and both servers, and publickey authentication must be enabled.

You also need server names, usernames and passwords for both servers **S1** and **S2**.

## Set up password-less login

Generate public keys on your home computer, by issuing the command:

    ssh-keygen -t rsa

Leave everything blank. If you wish, you can generate different keys for logging into **S1** and **S2**, and in that case you should save the keys in different files likes `id1_rsa` and `id2_rsa.`

Move the generated keys to the server:

    scp ~/.ssh/id_rsa.pub username1@S1:id_rsa.pub

Create the `.ssh` directory and append the key to the `authorized_keys` file.

{% codeblock lang:bash %}
ssh username1@S1                            # access S1
mkdir -p ~/.ssh                             # create .ssh directory
touch ~/.ssh/authorized_keys                # create file
chmod 644 ~/.ssh/authorized_keys            # give correct permissions
cat id_rsa.pub >> ~/.ssh/authorized_keys    # add public-key to file
{% endcodeblock %}

Repeat this procedure for **S2**, making sure to move the relevant files all the way through **S1** first. Remember to delete the `id_rsa.pub` file after you have added it to the `authorized_keys` file. 

    rm id_rsa.pub

You should then be able to log in to **S1** from your home computer without using your password. Test that this work seamlessly before moving on.

## On your computer

Create `~/.ssh/config` file to manage your connections. In the config file you should put the following:

{% codeblock lang:bash %}
Host S1nick
    Hostname S1
    port 22
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id1_rsa
    User username1

Host S2nick
    HostName S2
    port 22
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id2_rsa
    User username2
    ProxyCommand ssh -A S1nick nc %h %p
{% endcodeblock %}
The variables **S1nick** and **S2nick** are some short nick names for the two servers. This is convenient because servernames tend to be long and tedious to type. If you are using a university network you could e.g. set **S1nick** to "uni" and **S2nick** to "calc".

Now you can access **S1** with the command

    ssh S1nick

And server **S2** with,

    ssh S2nick

Voila!
