---
layout: post
title:  "My bibliography workflow"
date:   2015-09-28 22:13:00
categories: tools
---

This is just a quick post to explain how I will manage my bibliography from
now.

The tools I am/will using/use are : Jabref, git and bittorrentsync or any file sharing
system used as a binary storage. I heard about some git tools that can keep
track/manage huge binary files but I did not test them so far.

So I have a different bibfile (I am using the bibtex format) for each specific
domain. These bib files are under revision control system. Each bib file let us
say foo.bib, will have tis conrresponding directory foo/. This Directory will
contain the binary file pdf, epub or any other intersting file linked to the
material I am reading/listening (if it's an audiobook).

So when you read a book/paper or anything you have the material. It can be
a pdf or hardcover book. You enter the metada of the book in Jabref, generate
a bibtex key if you are going to reference this book later (it is always safe
to generate it) link the electronic version if any, create a link using the
digital object identifer (DOI) or point to amazon.com. Before linking any
electronic version do not forget to move it to the appropriate directory and
rename the file using the generated bibtexkey. Commit the changes.

In this workflow one important thing is your .gitignore file in order to avoid
annoying git status messages.

That's it.

