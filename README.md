# Learn git-svn

Learning git-svn according to the original [Pro-Git online
book](https://git-scm.com/book/en/v1/Git-and-Other-Systems-Git-and-Subversion).

The first problem that arises is the fact that the original googlecode.com project,
which was at the address http://progit-example.googlecode.com/svn/, does not
exist anymore (since Google Code has been shut down). I found that it can be
retrieved at [this archive
address](https://storage.googleapis.com/google-code-archive-source/v2/code.google.com/progit-example/repo.svndump.gz),
and have added the resulting file to this repository.

Once downloaded, the following steps should be taken to create the svn
repository (it is actually faster than what is done in the original
description):

```
$ mkdir /tmp/test-svn
$ svnadmin create /tmp/test-svn
$ gunzip repo.svndump.gz
$ svnadmin load /tmp/test-svn/ < repo.svndump
```

After this we can already clone the svn repo into a git-svn repo:

```
$ git svn clone file:///tmp/test-svn -s
```

Note that in the description in the book at this point it seems like all
branches are automatically checked out locally, but this was not the case when I
ran it. In particular, I get the following:

```
$ git branch -a
* master
  remotes/origin/my-calc-branch
  remotes/origin/tags/2.0.2
  remotes/origin/tags/release-2.0.1
  remotes/origin/tags/release-2.0.2
  remotes/origin/tags/release-2.0.2rc1
  remotes/origin/trunk
```

You can get to the state described in the book by checking out all branches
(perhaps it is better to do this one branch at a time, as it is needed).

## Reference for SVN to GitHub migration

Check out [this
link](https://dominikdorn.com/2016/05/how-to-recover-a-google-code-svn-project-and-migrate-to-github/)

