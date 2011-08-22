===============
Git Cheat Sheet
===============

-----------------------------
What I just learned about Git
-----------------------------

Settings
========

- list Git configuration::

    git config --list

- set configuration::

    git config --global --add user.name "John Doe"
    git config --add color.ui "auto"

  ``--global`` makes the setting global for all repos.

- show configuration::

    git config --get user.name

- some common settings:

    +------------+----------------------+
    |    name    |  meaning             |
    +============+======================+
    | user.name  | User name.           |
    +------------+----------------------+
    | user.email | User email.          |
    +------------+----------------------+
    | color.ui   | Use colors?          |
    +------------+----------------------+
    |core.editor | Which editor to use? |
    +------------+----------------------+

Local use
=========

- Create a repository::

    cd projDir
    git init
  
- Add files to repository::

    cd projDir
    git add file1 file2

  or

  ::

    git add *

- Status and log::

    git status
    git log

- Commit changes::

    git commit changedFile -m "Commit message."

  or

  ::

    git commit -a

  (opens editor and allows to change the commit message)

- remove file from version control:

  - also remove file from disk::

      git rm file

  - keep file on disk::

      git rm --cached file

- go back to last commited version::

    git checkout

Usage with central repository
=============================

- Create a repository on central server::

    git init --bare --shared foo.git
    chgrp -R dev foo.git  (optional)
  
  ``shared`` makes the repo group writable.

- push local repo to server::

    cd localRepo
    git push ssh://user@host.domain.tld/home/user/foo.git '*:*'

  (this pushes the local repo with everything to the server)
  
- after hacking, update repo on server::

    cd localRepo
    git push

GitHub
======

- create repository ``repoName`` from the web interface

- teach local repository about the remote one::

    cd repoName
    git remote add origin git@github.com:githubuser/repoName.git

- push files to GitHub::

    cd repoName
    git push

- to clone the GitHub repo::

    git clone git@github.com:githubuser/repoName.git newRepo

- push changes back to GitHub::

    cd repoName
    git push

Links
=====

- Git community book http://book.git-scm.com/
- Git with central sever: http://toroid.org/ams/git-central-repo-howto

TODO
====

- stashes
- notions (staging, head...)
- learn about branches
