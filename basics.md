
# Basics

When you open neovim, and type in `:help<enter>`, you find a detailed guide about it's usage, I highly recommend you check it out as well.
My introduction will contain more details about the configuration, and only the most essential features of text editing. 
The best way of mastering neovim is to use it, and gradually improve your workflow with it's features. For this process, I'll provide you core knowledge at the beginning of this document, and more advanced features in the end.

## Configuration

Configuration files are written in lua(or [vimscript](https://learnxinyminutes.com/docs/vimscript/), but you should have a good reason to go down that path).

On linux, you have to create a new folder `~/.config/nvim/`, your entrypoint is `~/.config/nvim/init.lua`. That's where most things will go for now.
Later, you will use more than one file for configuration, you have to put them into `~/.config/nvim/lua/`. 

Create `~/.config/nvim/init.lua`, and open it with your currently used text editor.

Open up a neovim instance, and experiment with everything I mention here, gradually improve your configuration as we proceed!

## UI

## Command-line commands

Type `:q<enter>`, and you just exited. Command-line commands always starts with `:`.
There are many useful command-line commands, you can use Tab key to autocomplete them, some examples you will use every day are:
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
This is the most important strength of vi. Moving around and reading code is what we do most of the time, so we should be efficient at it.

Forget two things:
 - arrow keys
 - mouse

Later I will explain why, but in short, keeping your hands on the letters, helps you keep focus, and makes your movements faster.

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

If you want to remap, add these lines to your `init.lua`, and restart your neovim:
```
vim.api.nvim_set_keymap("n", "é", "$",{})
vim.api.nvim_set_keymap("v", "é", "$",{})
```

In the first line, "n" means normal mode, "é" is the key we want to remap to, and "$" is our normal mode command to execute when "é" is pressed.

The second line is to do the same, for visual(text selecting) mode.

## Insert mode

Recognise the fact that in normal mode your cursor is not between letters, but on letters.
To insert after a letter, we use `a`, and to insert before a letter we use `i`.
Press a and start typing. To exist insert mode, press escape.

When you are in insert mode, forget about movement. Get used to moving around in normal mode, and only typing in insert mode.

If you want to start in a new line, press `o`.

## Delete
Delete single characters with `x`.

Delete lines with `dd`.

## Combine movement and action
Delete single word with `de`, or current and next line with `dj`.

You can combine lots of normal mode commands, and repeat them as well, some examples are:

`5dd` - delete the next 5 lines.
`10k` - move 10 lines up

You don't have to memorize these, keep them in muscle memory instead. Practice is key.
Try to use them every time you see some problem, try to find some more clever ways of combining actions and movements, and by practice, they become instinctive.

## Undo, redo

Press `u` to undo your last change, and `ctrl+r` to redo. (both in normal mode)

## Visual mode(text selecting)
Sometimes you want to select some text to copy, or delete, this is done in visual mode.
Press `v` and start moving around, you will see the selection. You can use `d` to delete the selected text.

## Clipboard
To copy and paste, you have a ton of options as well. In vi world, the term is "yank".
Press `y`, and some movement key, then press `p` to paste.
Yank a whole line with `yy`. Important to note here that `dd` also yanks the line to clipboard after delete.

By default, neovim uses it's own clipboard, to make it use the system clipboard, first check weather your nvim installation is capable of such thing.
You can do that by running `:echo has('clipboard')`. It should output 1, otherwise, [you have to troubleshoot your installation](clipboard.md).

Connecting nvim and system clipboard done by the following line in your config:
```
vim.opt.clipboard = "unnamedplus"
```

## Indent 
In case you want to move a line one indentation in or out, you can use the `>>` and `<<` normal mode commands.

This also works on visual selection.

A quiet annoying thing about indenting visual selected text is you lose your selection after indent.

To stay in visual mode after select, add these lines:
```
vim.api.nvim_set_keymap("v", ">", ">gv",{})
vim.api.nvim_set_keymap("v", "<", "<gv",{})
```

My preference on indentation settings are:
```
vim.opt.expandtab = false
vim.opt.tabstop = 4
vim.opt.shiftwidth = 4
vim.opt.softtabstop = -1
vim.opt.tabpagemax = 2
```

## Tabs, buffers
The file you open and edit, is called a buffer. This is the smallest unit in neovim UI. 
We have the ability to split our screen with `:split <filepath>`, or open multiple tabs with `:tabedit <filepath>`.
Navigation between buffers and tabs is done by command-line commands, and it's not very convenient by default, so here comes my tested setup:

Open file in new tab with `tt <filename><enter>`:
```
vim.api.nvim_set_keymap('n', 'tt', ':tabedit<Space>', { noremap = true, silent = false })
```

Open file in split view with `t$ <filename><enter>`:
```
vim.api.nvim_set_keymap('n', 't$', ':vsplit<Space>', { noremap = true, silent = false })
```
(`té` for my qwertz keyboard)

Navigation:
```
vim.api.nvim_set_keymap('n', 'th', ':tabfirst<CR>', {})
vim.api.nvim_set_keymap('n', 'tj', ':tabnext<CR>', {})
vim.api.nvim_set_keymap('n', 'tk', ':tabprev<CR>', {})
vim.api.nvim_set_keymap('n', 'tl', ':tablast<CR>', {})
```
`th` and `tl` moves to the last and first opened tab, and `tj`, `tk` is the next / previous tab.

Closing tab with `td`:
```
vim.api.nvim_set_keymap('n', 'td', ':tabclose<CR>', {})
```

There is a key called a "leader" key, which gives us more customization option.
Traditionally it's spacebar, so set it to space:

```
vim.g.mapleader = " "
vim.g.maplocalleader = " "
```

This way navigation between split windows becomes easy as well:
```
vim.api.nvim_set_keymap("n", "<Leader>h", "<C-w>h",{})
vim.api.nvim_set_keymap("n", "<Leader>j", "<C-w>j",{})
vim.api.nvim_set_keymap("n", "<Leader>k", "<C-w>k",{})
vim.api.nvim_set_keymap("n", "<Leader>l", "<C-w>l",{})
```
with `<space>` + h/j/k/l keys.

## Search
Search the current buffer with `/<search-term><enter>`.
Circle in the result list with `n` forward, and `N` backward.

```
vim.opt.incsearch = true
vim.opt.ignorecase = true
vim.opt.smartcase = true
```

`incsearch` shows potential matches in your buffer while you type, `ignorecase` let's you use lowercase letters in your search term, but with `smartcase`, if you use uppercase letters, you get a precise case sensitive match.

## Macros
Macros are an essential part of the vi experience.
You can record macro into "registers", and call them.

Usual workflow is the following:

Press `qa` to start recording your macro. When you are done, press `q` again.
Now you can call your macro, and replay your keystrokes with `@a`.

You can also combine normal mode commands here, and call your macro multiple times by typing `10@a`.

## Relative, absolute line numbers
Enable line numbers with:
```
vim.opt.number = true
```
It's also possible to set relative line numbers:
```
vim.opt.relativenumber = true
```
This way, you can jump to the exact line by number with `<numberofline>j`, `<numberofline>k`.

For [LSP](lsp.md) we can also set 
```
vim.opt.signcolumn = "number"
```
so error indicators will show up in the line number column when we finally configure our IDE functionality.

## Advanced movement

There are some more advanced movements I tend to use on a daily basis.
With `{` and `}` you can move between paragraphs.

To get to the beginning of the file, type `gg`, and `G` to get to the end.

Sometimes you move in the same file around, and you want to get back to the last cursor position fast. To do that, press `ctrl+o`. Circle to the other direction with `ctrl+i`

## Options
We have changed a couple options, but there is [more](https://neovim.io/doc/user/options.html).

Some essentials follows.

Persistent undo-redo. (Keeps track of your editing history after closing the file)
```
vim.opt.undofile = true
```

Disable mouse!
```
vim.opt.mouse = nil
```

No need to scroll until the end of screen, keeps your vision on the center of the screen. 
```
vim.opt.scrolloff = 8
vim.opt.sidescrolloff = 8
```
## Terminal + navigation setup
My favourite feature of neovim, is the built in terminal support.
Open one with `:tab ter`, now, when you are in insert mode, you can type in commands as you usually do, but in normal mode, you can copy and paste as you do in other types of buffers as well. In my opinion it is an extremely powerful feature, but we have to customize it as well, to make it even more useful.

Exit to normal mode with escape:
```
Keyboard.map("t", "<Esc>", "<C-\\><C-n>")
```

Open terminal in new tab:
```
vim.api.nvim_set_keymap("n", "ti", ":tabedit<Space><CR>:tab ter<CR>", {})
```

Open terminal in split window:
```
Keyboard.map("n", "to", ":botright vnew<Space><CR>:tab ter<CR>", {})
```


## Autocommand
Autocommands are a way to tell neovim to run certain configuration only for a certain kind of filetype.

There is built in spellchecking in neovim, but it is very annoying when turned on for every filetype, so I restrict it to just markdown:

```
vim.api.nvim_create_autocmd(
	{ 'BufReadPost' }, {
	pattern = '*.md',
	callback = function()
		vim.opt.spelllang={'en'}
		vim.opt.spell = true
	end
})
```

To apply your callback for multiple buffer types, use an array of patterns:

```
vim.api.nvim_create_autocmd(
	{ 'BufReadPost' }, {
	pattern = {"*.md", "*.txt"},
	callback = function()
		vim.opt.spelllang={'en'}
		vim.opt.spell = true
	end
})

```

## Keymap with callback
Mapping a function, instead of normal mode commands can be done by:
```
vim.api.nvim_set_keymap(<editor mode, usually "n">, <keys to press>, "", { callback = function()
        -- do things here
    end
})
```

## Custom commands
Define your command-line commands:
```
vim.api.nvim_create_user_command('Cpath',":let @+=expand('%')", {})
```
This one copies the file path of the currently opened buffer relative to the project root.

Custom command-line commands are always first letter capital!


