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
`readme.md`

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
I call it). The first state is the actual state of our file `readme.md`: this
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
```

```
    git add readme.md
```

```
    git commit -m "Added line number 2"
```

```
    echo "line number 3" >> readme.md
```

```
    git add readme.md
```

```
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
```

```
    git add readme.md
```

Not you change your mind and want to remove this last line of our file, but our
file/modification is already staged. Note that staged is the status of the file
when it is added but not commited yet. To come back to the previous version of
readme.md run:

```
    git reset HEAD readme.md
```

```
    git checkout -- readme.md
```

Now you are back on the previous state of the file.

Let us now assume that you want to undo the last two commits. Since in git we
do not want to re-write history, we just undo the commits by doing some
commits. This is how you should procede:

```
git revert HEAD~2..HEAD
```

This command will prompt you for commit message to explain why you are doing
it. Since you want to undo two commits (HEAD~2) you will be prompted by two
commit message. If you want to have only one single commit to explain why you
wat to go back to an older version, do:

```
    git revert --no-commit HEAD~2..HEAD
```

```
    git commit
```

If you do not want to edit commit message (I do not recommand it) run:

```
git revert --no-edit HEAD~2..HEAD
```

Now you want to branch. My rule is branch often, commit often. Every
time I want to do a modification that I am not sure or I do not want to alter
the initial file until I am really really sure, I create a branch. A Branch is
like a copy of your actual directory. By default you are in the master branch.
So for example to copy the master branch to another branch name test:

```
git branch test
```

This command will "copy" the branch master to the branch test. If you are not
sur in which branch you are type:

```
git branch
```

To switch from branch test

```
git checkout test
```

Let us now modify the file when we are in this branch and commit the
modification in this branch.

```
    echo "TEST: added a new line" >> readme.md
```

```
    git add readme.md
```

```
    git commit -m "TEST addons"
```

Come back to the branch master and see the difference between the files.

```
    git checkout master
```

```
    cat readme.md
```

Now that we are satisfied by the modificatio made in the branch test, let us
include/merge the modifications in the branch master and look at your
`readme.md` file.

```
    git merge test
```

```
    cat readme.md
```


These are more or less the git command I use everyday. I also use `git remote`
to sync my local repository to a distant one. To add a remote repository run:

```
     git remote add <name> <url>
```

I usually use `origin` as name and `https://github.com/user/test.git`. Be sure
you have created the repository in your github account in this case. Then push
everything to the repository by running:

```
    git push origin master
```

```
    git push origin test
```

If you want to clone an existing repository on a new computer for example:

```
    git clone https://github.com/7ahiry/test.git
```

If you want to get an update from a branch on a remote repository:

```
    git pull origin master
```

To update all branch run:

```
    git pull --all
```


If you have modified your file/directory and want to split the modification into different commits. 
You can do 
```
git add --patch filename.x
``` 

`(or -p for short)`, and git will begin breaking down your file in what it thinks are sensible "hunks" (portions of the file). You will then be prompted with this question:

```
Stage this hunk [y,n,q,a,d,/,j,J,g,s,e,?]?
```

And here the meaning of each option:

- `y` stage this hunk for the next commit
- `n` do not stage this hunk the next commit
- `q` quit; do not stage this hunk or any of the remaining ones
- `a` stage this hunk and all later hunks in the file
- `d` do not stage this hunk or any of the later hunks in the file
- `g` select a hunk to go to
- `/` search for a hunk matching the given regex
- `j` leave this hunk undecided, see next undecided hunk
- `J` leave this hunk undecided, see next hunk
- `k` leave this hunk undecided, see previous undecided hunk
- `K` leave this hunk undecided, see previous hunk
- `s` split the current hunk into smaller hunks
- `e` manually edit the current hunk
- `?` print help

If the file is not in the repository yet, do first `git add -N filename.x`. Afterwards you can go on with git add -p filename.x.

You can use than: `git diff --staged` afterwards to check that you staged the correct ones `git reset -p` to unstage incorrect hunks `git commit -v` to view your commit while you edit the commit message.

If you are not satisfied with the way git splitted your hunks, use the `e` manually edit the current hunk option. Delete the lines you to not want and commit. Deleting file portion in this case will not affect the change you have done. 
