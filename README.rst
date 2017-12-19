=========
simpledot
=========

``simpledot`` is a utility for managing dotfiles. You store them in a single
location, like a directory in iCloud Drive, Dropbox, or a ``git`` repository
and ``simpledot`` will automatically create symlinks to the correct location
when you run ``simpledot up``.

How does ``simpledot`` know where to create the symlink? Inside your dotfile
you include an 'annotation' line. For example, a ``vimrc`` might contain::

    """ dotfile @ ~/.vimrc
    set ts=4
    ... rest of vimrc ...

Likewise, your ``.bash_profile`` might contain::


    # dotfile @ ~/.bash_profile
    alias ls="ls -G"
    ... rest of bash_profile ...

Commands
========

* source - Specify directory that contains your annotated dotfiles
* list - List files in source directory and show whether they've been
  symlinked with a checkmark, or not, with an 'x'. ``list`` is the default
  command, so if you run ``simpledot`` without a different command specified,
  then ``list`` will be run
* up - Create symlinks
* down - Remove any symlinks that were created


How to Use
==========

1) Copy your dotfiles into a directory (iCloud Drive, Dropbox, or a ``git``
repo)

2) Register your dotfiles directory with simpledot using the ``simpledot
source`` command. Make sure your dotfile contain annotation which describe
where the symlink should be created.

3) Run ``simpledot up`` to create symlinks

4) Run ``simpledot`` to verify that symlinks were created. You should see
a checkmark for each dotfile symlink that was created::

    $ ./simpledot list
    Source: /Users/rick/.simpledot

    ✓ bash_profile         -> /Users/rick/.bash_profile
    ✓ ssh_config           -> /Users/rick/.ssh/config
    ✓ vimrc                -> /Users/rick/.vimrc
    ✓ gitconfig            -> /Users/rick/.gitconfig
