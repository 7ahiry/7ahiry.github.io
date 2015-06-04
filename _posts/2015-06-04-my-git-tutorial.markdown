---
layout: post
title:  "My git tutorial"
date:   2015-06-04 22:13:00
categories: tools
---

This post is not meant to be a real tutorial. I will just put here the git
command I am used to use and try more or less to explain them. If you need
a complete tutorial, you can find a lot of them by using your favorite internet
research website.

I have become a huge fanatic of git. Now, everytime I enter a directory, the
first question I am asking is: Am I going to produce some text ? If the answer
is yes, then the first command I run in this directory is:

```
git init
```

Even if I am not going to use revision control, this is a safety belt. you
never know.

Strating from there, I am just creating my text file. Let us create a file
readme.md

```
echo "My readme" > readme.md
```

You have made some modification to your working copy. In fact you have added
a new file. If you do not have a fancy prompt that tells you that, run the
following command to see the status of your working directory.

```
git status
```

A file/modification can have three state in your git repository (that is how
I call it). The first state is the actual state of our file readme.md: this
file or modification is untracked. In order to track the file, that means
include it in your git repository run:

```
git add readme.md
```


