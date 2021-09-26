---
title: Git Bisect - The best thing to find the commit that introduced a bug!!!!
---

A while ago I had to fight an unexpected bug in production. I was not alone in this fight. I was with a co-worker that introduced me the Git Bisect. And since then I have been in love with it!

Git bisect is a git command that uses binary search to find the commit that introduced a bug. Of course, to it work you need to know a commit where the bad was not there yet.

You can start with:

```
git bisect start
```
Then you should specify that this version has the bug with

```
git bisect bad
```

And you should specify the last version that you know it's right:

´´´
git bisect good v2.6.13-rc2
´´´
The git bisect will pull a version in the middle on this two. You should run the code and confirm if in this version you have the bug or not. Use the following commands:

```
git bisect bad
```
or 

```
git bisect good
```

It will help the git bisect reduce the branches that need to be analysed. Keep this process until there will be no more versions to analyze. 





