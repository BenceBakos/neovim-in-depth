
# Neovim basics

## Introduction
Neovim is an extremely customizable terminal text editor, which puts fun back into software development, and can provide a base to build your productive tool for the everyday tasks.
However, mastering it can take some time and practice, and not every possibility is obvious for a beginner.

This guide will hopefully make this process easier for you.

Every section of this document will unfold little parts I think worth mentioning and learning. We are moving from simple concepts, like basics of text editing and navigation, to the advanced stuff like [LSP](https://neovim.io/doc/user/lsp.html), and useful plugins. Almost every seciton will contain my take on customizing certain features. Feel free to experiment, and use these as no more than inspiration to build your own experience.

Obviously this is just the surface, take as many resources as you can, and build your own experience.

Please note that neovim by itself is just a skeleton, not very useful by itself. From day 0 you should keep your configuration close to you, always ready to tweak and change as you see your workflow evolve around neovim and plugin features.

## Installation
Always [install](https://github.com/neovim/neovim/wiki/Installing-Neovim) the latest version.

## Configuration

Configuration files are written in lua(or [vimscript](https://learnxinyminutes.com/docs/vimscript/), but you should have a good reason to go down that path).

On linux, you have to create a new folder `~/.config/nvim/`, your entrypoint is `~/.config/nvim/init.lua`. That's where most things will go for now.
Later, you will use more than one file for configuration, you have to put them into `~/.config/nvim/lua/`. 

Create `~/.config/nvim/init.lua`, and open it with your currently used text editor.


