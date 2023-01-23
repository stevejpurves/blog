---
title: The Littlest JupyterHub
description: ''
date: '2022-11-10T12:30:23.911Z'
name: the-littlest-jupyterhub
oxa: oxa:DOHMeg040aVXqR51yjBy/nzKQJcq6LrqD6AHLFoaY
subtitle: A semi-random walk through the documentation to setup some TLJH's
short_title: ''
tags: []
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/HpNoX5Zd2G9qMslnhXit.1","tags":[]}

# Setting up on AWS

## Get the hub up and running

1. follow the [AWS Installation Guide](https://tljh.jupyter.org/en/latest/install/amazon.html#step-3-install-conda-pip-packages-for-all-users), except do not add the bootstrap script as user data, instead
2. launch an new instance - I used ubuntu 18 as per the docs
3. ssh in add your key to `authorized_keys`
4. ssh in again to check and run the bootstrap script manually
5. once it is done, access your instance via `http`
6. set a password for your admin user
7. play around on your server and in the admin panel

## Secure via `https`

1. follow the docs here: [Enable HTTPS](https://tljh.jupyter.org/en/latest/howto/admin/https.html)

That was easy

## Update Python

1. follow the docs here: [Upgrade Python](https://tljh.jupyter.org/en/latest/howto/env/user-environment.html#upgrade-to-a-newer-python-version)

## Containers & Named Servers

1. [Understand what this means](https://jupyterhub.readthedocs.io/en/stable/reference/config-user-env.html#multi-user-hosts-vs-containers)
2. Use [DockerSpawner](https://github.com/jupyterhub/dockerspawner) with [TLJH](https://ideonate.com/DockerSpawner-in-TLJH/)
3. Enable [Named Servers](https://jupyterhub.readthedocs.io/en/stable/reference/config-user-env.html#named-servers)

