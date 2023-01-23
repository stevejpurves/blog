---
title: T21 Tutorial Prerequisites
description: ''
authors:
  - userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    name: Steve Purves
    orcid: 0000-0002-0760-5497
    corresponding: false
    roles: []
    affiliations: []
date: '2021-04-19T10:12:25.209Z'
name: t21-tutorial-prerequisites
oxa: oxa:DOHMeg040aVXqR51yjBy/Cdn2dvJB9QWFzAZ0BbMe
tags: []
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/4pTlKb9FBRk2GsjJK94E.1","tags":[]}

### Version Control for Scientists

Key information and links:

- [Tutorial Live Stream on Youtube](https://www.youtube.com/watch?v=S4uqsbV-gxY)
- [Tutorial Channel on Slack](https://swung.slack.com/archives/C01RGGXNR9P)

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/mNo3VGcm50rGkEwTUebU.2","tags":[]}

### Tutorial Setup

Setup for this tutorial is relatively light. We’ll be using lightweight content and generating most of our examples as we go.

### Install git

If you are on mac or linux it’s very likely you already have git installed on your system. To check open a terminal and type `git version`

```{figure} images/DOHMeg040aVXqR51yjBy-Rl168kPSUMLyL8F09wOU-v1.png
:name: d48e65eb
:align: center
:width: 100%
```

If not then you can install git by following the instructions for you platform [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

NOTE: Windows users, you are likely to have to install git unless you are already using it. Please make sure that you can access git from the command line or a

### Install Visual Studio Code

Using a GUI tool can really help both in terms of productivity and keeping track on what is going on in a repository, especially when working with others.

We are going to use Visual Studio Code and particularly on of the Git extensions available there. I’ve chosen VSCode as it’s cross plaform and the Git extension looks visually very similar which you’ll find in other UI based git clients like; [SourceTree](https://www.sourcetreeapp.com/) or [Kraken](https://www.gitkraken.com/).

For the tutorial, please [install VSCode on your computer](https://code.visualstudio.com/download) ahead of time, open it and make sure you are happy it works.

Feel free to also install the Git Graph Extension from the Extension Store within VS Code but i’ll also go over this step during the tutorial.

```{figure} images/DOHMeg040aVXqR51yjBy-ihYhdpMXlEpbTeawmY6n-v1.png
:name: 218c508d
:align: center
:width: 100%
```

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/m2UIC9tRkTim7bAov32F.2","tags":[]}

### Sign up for github

If you don’t already have a github account then sign up for a free account [here](https://github.com/).

```{figure} images/DOHMeg040aVXqR51yjBy-1XDE7fdnxC93l28wSuvF-v1.png
:name: a0790fa8
:align: center
:width: 70%
```

Then follow [these instructions](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) to setup a new SSH key on your GitHub account.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/fMMAG79i13OFdYNEJPeE.1","tags":[]}

### Signup for Curvenote

We’ll be looking at Jupyter Notebooks and some of the issues around versioning these with tools like git. There are alternative approaches one of which is Curvenote, which we’ll take a look at.

```{figure} images/DOHMeg040aVXqR51yjBy-b0ikthCp3GdBVWKMqfD3-v1.png
:name: 5e5af49f
:align: center
:width: 70%
```

If you are a chrome user, and would like to follow along you can get setup ahead of time:

1. Signup for a free Curvenote account here: <http://curvenote.com>
2. Install the Curvenote Chrome Extension here: [Google Chrome Store](https://chrome.google.com/webstore/detail/jupyter-versioning-commen/egkbkefajoeehbmjgelpmdnpgnleknka)

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/CP6y9JHDRYyqqxacewQb.1","tags":[]}

### Download DVC

We’ll take a look at a Data Versioning tool called DVC.

```{figure} images/DOHMeg040aVXqR51yjBy-nBRvem38tIHnuv5jwyuH-v1.png
:name: 0af19ffe
:align: center
:width: 70%
```

In order to follow along and try this out you’ll need to install DVC locally. It is available via pip, but for simplicity’s sake (and so we get all the optional add ins) please install from their website: <https://dvc.org/>

