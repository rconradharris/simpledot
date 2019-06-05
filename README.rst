=========
simpledot
=========

``simpledot`` is a utility for managing dotfiles. You store them in a single
location, like a directory in iCloud Drive, Dropbox, or a ``git`` repository
and ``simpledot`` will automatically create symlinks to the correct location
when you run ``simpledot up``.

By default, ``simpledot`` will symbolically link files that start with a dot
from your source location to your home directory. For most dotfiles this
behavior works fine; however, some dotfiles need to be placed in a different
location.

In these cases, you can override the destination by providing an 'annotation'
at the top of the dotfile which contains the destination location. An example
of this would be an ``ssh`` config, perhaps called ``ssh_config``, in your
source location::

    # dotfile @ ~/.ssh/config
    Host myserver
        Hostname myserver.example.com
        User alice

This would create a symlink from ``<SOURCE>/ssh_config`` to ``~/.ssh/config``.


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
