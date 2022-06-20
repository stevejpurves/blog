---
title: Getting Started with the Curvenote CLI
description: ""
authors:
  - userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    name: Steve Purves
    orcid: 0000-0002-0760-5497
    corresponding: false
    roles: []
    affiliations: []
date: 2021-04-30T13:44:07.350Z
name: getting-started-with-the-curvenote-cli
oxa: oxa:DOHMeg040aVXqR51yjBy/QVWrssqduv5N7Cvlvst1
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/C6Uc3CcwJ9Em4172QEJR.2"}

## Curvenote is on PyPi 🐍

We recently published a python client library and command line interface on pypi .

Find it at: <https://pypi.org/project/curvenote/>

```{figure} images/DOHMeg040aVXqR51yjBy-whc7KFWpINYGFQS0eURD-v1.png
:name: 85d242e1
```

This equips python coders with some wide ranging API access capabilities that we will continue to extend.

The CLI also allows anyone comfortable on the command line to run a small set of queries, which we’ll also be extending as we develop further.

To get started with the cli and/or client, create your virtual environment as usual and install using `pip`.
```
$ mkdir working
$ cd working
$ python -m venv env
$ source env/bin/activate
(env)$ python -m pip install curvenote
(env)$ python -m curvenote --version
Curvenote CLI Version 0.0.10
```

```{iframe} https://www.loom.com/embed/8f54fdea81704346baf9be0186c484dc
:label: bYGCwSYjEP
:align: center
:width: 70%
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/h2IySgdyOMbmTB2prlxG.1"}

## API Access

Right now there is now way to get a long lived API key from Curvenote (Coming Soon!) but we can get a daily API key from your browser. It’s a little involved if you are not used to peeking inside of your browser tools, so i’ve recorded a short video to show how.

```{iframe} https://www.loom.com/embed/d0f265e99c9645e19abf42342738dd6e
:label: x9NUQX5uy7
:align: center
:width: 70%
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/3jprBzXa7p5MvWZHBkyH.1"}

## Downloading Latex

One of the most useful CLI functions right now is the `pull-as-latex` command which let’s you download any article as a local LaTeX project which you can tweak and build locally.

```{iframe} https://www.loom.com/embed/da006c7788c44a6281fd4b91e83300ac
:label: XpInezXsAO
:align: center
:width: 70%
```

