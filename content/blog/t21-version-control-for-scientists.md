---
title: T21 Version Control for Scientists
description: Version Control for Scientists - some background and an overview of
  my Transform 2021 Tutorial
authors:
  - userId: fI5cWFyZPEZCTpIHdqX5H8OU3Iv1
    name: Steve Purves
    orcid: 0000-0002-0760-5497
    corresponding: false
    roles: []
    affiliations: []
date: 2021-04-19T09:38:19.728Z
name: t21-version-control-for-scientists
oxa: oxa:DOHMeg040aVXqR51yjBy/EWRLSoFX8YCKauhnw1YS
---

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/rGhErt4nStvNKrnM6hha.1"}

## Introduction

This week is the [Software Underground TRANSFORM 21 Unconference](https://softwareunderground.org/events/transform-2021) a combining tutorials, a hackahton with unconference events and SWUNG’s first AGM.\
\
On Thursday (22nd April) at 11am UTC, I’ll be giving a tutorial on [Version Control for Scientists](https://www.youtube.com/watch?v=S4uqsbV-gxY)! where we’ll spend time taking a slower and more detailed look at version control tools than many scientists usually have the time for.

Ahead of then I’d like to set out some background and what I’ll cover in the event.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/5ZsB4O7dtrfrstT6fTpk.1"}

## Why scientists need version control

Use data in science is increasing. There is also an increasing need to reliably be able to reproduce scientific results and thankfully a growing awareness of how important this is to scientific progress and integrity. Reproducible workflows need version control to provide an audit trail and references to immutable versions of code, data and other content that can be accessed and referenced in future.

Although by embracing version control scientists not only gain the possibility of implementing reproducible workflows and experiments, they gain a tool that can significantly help with day to day work; providing the confidence to ruthlessly change code, a medium through which to collaborate and share that can boost productivity and save them from losing work.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/LKpM5hVFDO8OozbrJgI8.1"}

## But version control is difficult

Increasingly scientists are being pushed to learn and use tools that were built and are predominantly used by developers and engineers. These tools excel in use cases they were intended for versioning code and text files.

They struggle more when dealing with larger data files or structured data like json, where the real content is held within a data structure that can change independently. A prime example of the latter are Jupyter Notebooks which are difficult to work with collaboratively in git.

Apart from this scientists often have the huge challenge of learning version control tools in fits and spurts, often getting comfortable enough to be able to pull and push code but not having the chance to learn about fundamentals, or develop good enough mental models of what is going on in tools like `git` to help them navigate problems or use the more advanced features of the tool fully.

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/A35XEYtZ1UlzesP4UtvR.1"}

## What are scientists burning Git Questions?

A few weeks ago I shared a[ Q&A on slido](https://admin.sli.do/event/lmmuqiwq/questions) to canvas for what some of the biggest git questions people had were. This was shared on the SWUNG slack channel, and on twitter but the modest response showed up some interesting questions.

The responses reflect that people in swung range from git curious, through to practitioners who are looking to understand how to use git in a better way. I’ve used the responses to guide structuring the tutorial and I’ll aim to include the following.

- Getting Started with Git
- Different ways to use git
  - Command Line
  - VSCode
  - Github
- Working alone
  - Common commands
  - The stash
  - Best Practices
- Working with others
  - Distributed repos
  - Remotes
  - Github
    - Forks
    - PRs
  - CI/CD
- Up close with specific Git Commands
  - commit amend
  - log
  - merge
  - rebase
  - reset & revert
- Advanced Topics
  - Dealing with a Large Changeset & Atomic Commits
  - Squash
  - Editing the git log

+++ {"oxa":"oxa:DOHMeg040aVXqR51yjBy/6EaNrFPnIMKjNnF8QXLf.2"}

## About the tutorial

You can find how to get setup for the tutorial [here](https://curvenote.com/@stevejpurves/blog/t21-tutorial-prerequisites). I work exclusively on MacOS and Linux systems so have limited recent experience of windows based tools. We’ll be focussing on cross platform aspects of git and cross platform tools rather than the windows specific git GUI.

I’ll want to make the tutorial as hands on as possible, so you should be able to (pause youtube maybe) and follow along from you terminal. I’ll probably be using Visual Studio Code heavily as it’s inbuilt terminal pane gives us a nice way to have terminal+folder-tree+files open at once on the screen.

The tutorial will be in the following order:

1. Intro and setup
2. Getting Started with Git
3. Different ways to use git
4. Working alone
5. Working with others - Github
6. Up close with specific Git Commands
7. Advanced topics (time allowing)
8. Other Version Control systems
   1. Curvenote for Jupyter Notebooks
   2. Data Versioning

