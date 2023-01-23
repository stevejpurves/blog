---
title: The Jupyter CLI and Subcommands
description: ''
date: '2022-09-28T08:48:30.231Z'
name: jupyter-cli-and-subcommands
oxa: oxa:DOHMeg040aVXqR51yjBy/XcdKfHK3ad0fFFGAgkTa
short_title: ''
tags:
  - jupyter
  - code
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/VQCxtFAG9icd7eKfPeFJ.1","tags":[]}

## CLI

The `jupyter` command is a CLI that allows you to explore configuration information, run specific subcommands as well as start the familiar notebook and lab environments.

```{figure} images/DOHMeg040aVXqR51yjBy-yX0KEgxJEfopcZKJxMgm-v1.png
:name: t9M8IbM7Ex
:align: center
:width: 100%
```

Subcommands are added to the Juptyer CLI by installing different packages in your python environment, with the exception of the `notebook` which comes bundled when the `jupyter` package is installed. The `lab` and `lite` subcommands are added by installing the `jupyterlab` and `jupyterlite` packages respectively.

Unfortunately, there is no option on the CLI to list the available subcommands.

`notebook` and `lab` start two different server environments, each of which run their own webserver and load extensions from two completely independent extension systems.

### Classic Notebook

In the classic notebook, extensions can be listed and manipulated using the `jupyter nbextension` command.

```{figure} images/DOHMeg040aVXqR51yjBy-1xxIKTna07Fq2SF1uVcY-v1.png
:name: Km8uto9e3y
:align: center
:width: 100%
```

### Jupyter Lab

In the lab environment, a different subcommand is used to list and manage the lab extensions, `jupyter labextension`.

```{figure} images/DOHMeg040aVXqR51yjBy-coXXTvjQO3gyQFayHF9g-v1.png
:name: k9LrnAcvuv
:align: center
:width: 100%
```

In either case, this allows you to see which extensions you have available when starting a Jupyter server with either the Classic Notebook or Lab interfaces.

