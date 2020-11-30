---
author: "Jacopo Schiavon"
title: "A short guide for blog posters"
date: "2020-11-30"
description: "Short tutorial on how to create blog posts for paperinik."
tags: ["guide"]
categories: ["guide"]
series: ["Guide"]
ShowToc: true
TocOpen: true
weight: 2
---

_Brief guide to add blog post to Paperinik's blog_


The website is hosted in a [Github repository](https://github.com/mascaretti/paperitivo). To allow contribution from everyone, we will use the standard git collaborative framework based on forks and pull requests.

## Setting up the fork and the local repository

The first step, thus, is to fork the repository: from the repository page, in the top right corner of the page, press the Fork button to create a fork on your account and then clone the forked repository on your local machine. You can easily do this by opening a terminal or a Git Bash[^1] window in the location where you want the repository to be located and issuing 
```
$ git clone https://github.com/<yourname>/paperitivo.git
```
Note that here and in the following the $ symbol is used to indicate the input of the command shell (it should not be written in the terminal window) and is opposed to the > symbol which indicate the output of the shell.

[^1]: If you don't know how to use git or git bash, a very comprehensive introduction to the former is [here](https://git-scm.com/docs/user-manual), and [here](https://git-scm.com/doc) you can also find some introductory videos. 
	Git Bash is a very small program that allows windows user to issue the same commands that linux users will give in the terminal, allowing to type the commands only once. It is installed directly when you install git, and can be opened by right-clicking in the folder where you want to use git.

When the cloning operation is done, move in the folder with the repository and configure the upstream url. You can do this by issuing:
```
$ git remote add upstream https://github.com/mascaretti/paperitivo.git
$ git remote -v
> origin 		https://github.com/<yourname>/paperitivo.git (fetch)
> origin		https://github.com/<yourname>/paperitivo.git (push)
> upstream	https://github.com/mascaretti/paperitivo.git (fetch)
> upstream	https://github.com/mascaretti/paperitivo.git (push)
```

With this, your setup is complete.

## Adding a new post
When you want to add a new post, navigate to your local repository and create a new file in `content/posts`.
You can copy and rename one of the already created posts, for instance this one, in order to follow the structure. Don't delete any of the already existing files.

If you need to add some images, you can place those in the folder `assets/images/`, possibly creating a subfolder for your post in order to keep stuff organized.

When you are done writing, you can open a terminal in the folder of the repository (or a git bash window if you are on windows) and issue the following commands:
```
$ git add content/posts/<yourpost>.md
$ git commit -m "a short message that identifies your commit"
```
As a message for the commit, you can write some info on the post, for instance "added post on the paperinik in XX/XX/2020" or something similar. You can later modify your file and commit it again following the same procedure.

## Syncing the fork with upstream
When you are done and you want to publish your post, first you should sync your local copy of the repository with the upstream one, in order to have the latest version of the website.
To do so, you should first fetch the upstream repository commits:
```
$ git fetch upstream
```
Now the upstream work should be stored in a local branch called `upstream/master`. 
We first switch back to our local master branch by issuing
```
$ git checkout master
```
and then we perform the actual merge: this will put all the stuff from the upstream repository (the common one) to your local one, adding your local changes.
```
$ git merge upstream/master
```
When this is done, you should push your work to the online fork of the repository
```
$ git push origin master
```
This will ensure that the online version of your fork will be updated with your last work (and also with the work done in the common repository).
Then, open the github page of the common repository (the one available [here](https://github.com/mascaretti/paperitivo)) and navigate to the [Pull Request](https://github.com/mascaretti/paperitivo/pulls) tab. There, you can push the "New pull request" button.

![Creating a new pull request: the compare page](/assets/images/posting-guide/compare-page.png)

A "Compare Change" page will open, from where you can check what you are trying to accomplish. Press the "compare across forks" link and select your fork. 

![Creating a new pull request: select your fork](/assets/images/posting-guide/compare-forks.png)

Review the changes to avoid any error and finally press "Create pull request" and finally complete the form adding a brief explanation (if needed).

Almost all this topics are described in wide detail in the GitHub Docs, for instance [How to configure a remote for a fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork), [How to sync a fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork) and [How to create a pull request](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request-from-a-fork).



