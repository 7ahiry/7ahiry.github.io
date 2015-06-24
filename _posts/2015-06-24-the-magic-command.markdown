---
layout: post
title:  "The magic command"
date:   2015-06-24 09:41:00
categories: tools
---

Since I am using the my terminal all of the time, I have tried to make it
execute comment at the speed of my thoughts. Lucky terminal, my thoughts are
slow !!!

The first thing I have done is to create aliases and turn all the frequently
used command in a one-letter command. For example, I turn **firefox** into
**f**. In fact, when possible, I create a symlink in my **$HOME/bin** directory
to allow the command to be called from my lancher.

But the most useful command I have is **o**, for **xdg-open**. This is a killer
one. Like the open command in OSX. Just install it, and in my case create the
association between file type and application in
**~/.local/share/applications/mimeapps.list** and you are done. Now opening
a file (default action) should be as easy as: **o file**. Whatever file is, it
will use the default program I have defined.

My **o** command in not just a symlink to **xdg-open**, in fact it is a script
since I also want it to handle specific files that are not handled by the
**xdg-open** command such as the archive files.

Now my terminal is executing command at the speed of my thoughts.
