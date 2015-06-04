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
Now, your file is tracked (indexed ?). This is the second state of
a file/modification. You can now publish/commit this trackd file to your git
repository. Commiting, for me, means that you have reached a milestones in your
editing process. In our case the milestone is the the kickoff. So, to commit
your file/modification just run:

```
git commit -m "This is our first commit"
```

If you do not know what is happening in your git repository, just run git
status. Note that you can create/modify files and add them before commiting to
make your commit consistent.

Now let us modify our file

```
echo "line number 2" >> readme.md

git add readme.md

git commit -m "Added line number 2"

echo "line number 3" >> readme.md

git add readme.md

git commit -m "Added line number 3"
```
We are now entering the real power of git. We have done 3 commits. In orderto
see them just type:

```
git log
```

There are many other ways to see the commit history of your repository. You can
try so graphical interface for this.

Now let us modify our file in this way:

```
echo "line number 4" >> readme.md

git add readme.md
```

Not you change your mind and want to remove this last line of our file, but our
file/modification is already staged. Note that staged is the status of the file
when it is added but not commited yet. To come back to the previous version of
readme.md run:

```
git reset HEAD readme.md

git checkout -- readme.md
```

Now you are back on the previous state of the file.

Let us now assume
