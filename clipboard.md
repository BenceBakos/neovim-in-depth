# Troubleshoot clipboard support
**Feel free to contribute your solution to a specific scenario!**
To see weather your neovim installation supports system clipboard, you can run `:echo has('clipboard')`.
If the result is 1, you can set neovim to use the system keyboard with:

```
vim.opt.clipboard = "unnamedplus"
```

## Linux

### X
Usually the solution is to install `xclip` or `xsel`.

### Wayland
Get `wl-clipboard`!


## References
 - [ Copying to/from system clipboard doesn't work #2889 ](https://github.com/neovim/neovim/issues/2889)
