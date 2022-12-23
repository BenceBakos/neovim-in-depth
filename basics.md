
# Neovim basics

## Introduction
Neovim is an extremely customizable terminal text editor, which puts fun back into software development, and can provide a base to build your productive tool for the everyday tasks.
However, mastering it can take some time and practice, and not every possibility is obvious for a beginner.

This guide will hopefully make this process easier for you.

Every section of this document will unfold little parts I think worth mentioning and learning. We are moving from simple concepts, like basics of text editing and navigation, to the advanced stuff like [LSP](https://neovim.io/doc/user/lsp.html), and useful plugins. Almost every seciton will contain my take on customizing certain features. Feel free to experiment, and use these as no more than inspiration to build your own experience.

Obviously this is just the surface, take as many resources as you can, and build your own experience.

Please note that neovim by itself is just a skeleton, not very useful by itself. From day 0 you should keep your configuration close to you, always ready to tweak and change as you see your workflow evolve around neovim and plugin features.

Neovim is the descendent of vim, which is the descendent of vi. Vi is available on all linux systems, knowing how to use it is a very useful skill. I will distinguish vi and neovim, so you know what features are available in vi, and what features in both.

## Installation
Always [install](https://github.com/neovim/neovim/wiki/Installing-Neovim) the latest version.

## Configuration

Configuration files are written in lua(or [vimscript](https://learnxinyminutes.com/docs/vimscript/), but you should have a good reason to go down that path).

On linux, you have to create a new folder `~/.config/nvim/`, your entrypoint is `~/.config/nvim/init.lua`. That's where most things will go for now.
Later, you will use more than one file for configuration, you have to put them into `~/.config/nvim/lua/`. 

Create `~/.config/nvim/init.lua`, and open it with your currently used text editor.

## Basics
Neovim is a Terminal User Interface - TUI, so open up a terminal emulator, run `nvim`.

For the basics, you can type `:help<enter>`, I highly recommend you check it out, but I will cover everything important as well.

## Command-line commands

Type `:q<enter>`, and you just exited. Commands always starts with `:`.
There are many useful commands, you can use Tab key to autocomplete them, some examples you will use every day are:
`:w` - save
`:q` - quit
`:q!` - force quit, when you modified a file, but you want to exit without save
`:wq` - save and exist in one go
`:wqa` - save every buffer, and exit

`:edit <path>` open file 

Later we will see more advanced examples, as well as define our own commands.

## Modes

Open up a text file, with a couple of lines.
```
$ nvim <text-file-path>
```
or if you are already inside neovim, use the `:edit <text-file-path>` command.

There are multiple "modes" in vi, most notably
 - normal
 - insert
 - visual
 - command

If you are just opened a text file, it means that you are in normal mode.

Press `i`, start typing, you will see that in the bottom-left corner, `--INSERT--` appeared, that's what mode you are in.
To get back to normal mode, press escape.

## Switching between modes

I highly recommend you remap your capslock or some other unused key to capslock, because you will press it a lot.

On linux, with x window server, the easiest way is to run
```
setxkbmap -option caps:escape
```
undo this change:
```
setxkbmap -option
```

### Movements
This is the most important strength of vi. Moving around and reading code, is what we do most of the time, so we should be efficient at it.

Forget two things:
 - arrow keys
 - mouse

Later I will explain why, but in short, keeping your hands on the letters, helps you keep the focus, and makes your movements faster.

For basic up-down-left-right movements we user `h j k l`
```
 k
h l
 j
```
Get used to it by practicing moving around.

[This game](https://vim-adventures.com/) can help you.

We can also jump between words, with 
`e` - end of next word
`b` - beginning of previous word
`w` - beginning of next word


To get to the beginning of the line, press `0`, and `$` to get to the end fast.

For  `qwertz` keyboards, `$` is unpractical, I usually map this functionality to `é`(key next to l).

If you want to remap, add these lines to your `init.lua`:

```
vim.api.nvim_set_keymap("n", "é", "$",{})
vim.api.nvim_set_keymap("v", "é", "$",{})
```

In the first line, "n" means normal mode, "é" is the key we want to remap to, and "$" is our normal mode command.

The second line is to do the same, for visual(text selecting) mode.

## Replace
r,R
## Clipboard
system setup
## Combining movement and action
de, dé 
## Insert mode
a,i,o
## Visual mode(text selecting)
## Indenting 
staying in visual mode, indenting line without selecting
## Tabs, Windows, Terminal
## autocommands
## options
## Keymap with callback
## Other useful settings
## Custom commands
## macros
