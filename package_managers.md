# Package managers

Called this section "package managers", but it's really "plugin managers". Plugins in neovim are publicly hosted git repositories, there is no central database to search, but usually they are on github, and you can find the good ones discussed on [Reddit](https://www.reddit.com/t/neovim/).

Plugin managers clone plugins into `~/.local/share/nvim/site`, so you can `require` them for further configuration in your `~/nvim/`.


## savq's pkg.lua

72 lines of lua code is all you need to do the basics of plugin management. @savq is the creator of [paq-nvim](https://github.com/savq/paq-nvim), but he's dotfiles (used to) contain  [this simple solution](https://github.com/savq/dotfiles/blob/63cf083ccfdddf58758c6c7837c60c7c651ae8e3/nvim/lua/pkg.lua). Download it and put it in your `~/.config/nvim/lua` folder, and you can use it by:

```
---- Plugins
require 'pkg' {
	'williamboman/mason.nvim';
    ...
}
:install()
:update()
:clean()
```

After that, you simply `require` the packages for further configuration:
```
require("mason").setup()
```
