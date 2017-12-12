=========
simpledot
=========

``simpledot`` is a utility for managing dotfiles. You store them in a single
location, like a directory in iCloud Drive, Dropbox, or a ``git`` repository
and ``simpledot`` will automatically create symlinks correct location when you
run ``simpledot up``.

How does ``simpledot`` know where to create the symlink? Inside your dotfile
you include an 'annotation' line. For example, a ``vimrc`` might contain::

    """ dotfile @ ~/.vimrc
    set ts=4
    ... rest of vimrc ...

Likewise, your ``.bash_profile`` might contain::


    """ dotfile @ ~/.bash_profile
    alias ls="ls -G"
    ... rest of bash_profile ...

Commands
========

* source - Add a directory which contains files to symlink
* list - List what will be symlinked
* up - Add symlinks across filesystem
* down - Remove any symlinks that were created


How to Use
==========

1) Copy your dotfiles into a directory (iCloud Drive, Dropbox, or a ``git``
repo)

2) Add directory to `dotfiles` using `source` command

3) Annotate your dotfiles with ``dotfile @ <dst>`` somewhere in the file,
   for example, your `vimrc` might contain::

    """ dotfile @ ~/.vimrc

4) Run ``simpledot up`` to create symlinks

5) Run ``simpledot list`` to verify that symlinks were created. You should see
a checkmark for each dotfile::

    $ ./simpledot list
    Source: /Users/rick/.simpledot

    ✓ bash_profile         -> /Users/rick/.bash_profile
    ✓ ssh_config           -> /Users/rick/.ssh/config
    ✓ vimrc                -> /Users/rick/.vimrc
    ✓ gitconfig            -> /Users/rick/.gitconfig
