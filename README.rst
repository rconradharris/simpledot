=========
simpledot
=========

Simple dotfiles management for use with iCloud Drive or DropBox.

Commands
========

* source - Add a directory which contains files to symlink
* list - List what will be symlinked
* scatter - Scatter symlinks across filesystem
* gather - Gather symlinks across the filesystem (cleanup)


How to Use
==========

1) Copy your dotfiles into a directory

2) Add directory to `dotfiles` using `source` command

3) Annotate your dotfiles with 'dotfile @ <dst>' somewhere in the file,
   for example, your `vimrc` might contain::

    """ dotfile @ ~/.vimrc

4) Run `simpledot scatter` to create symlinks
