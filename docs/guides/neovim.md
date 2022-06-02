# Neovim

This guide is not about Vim in general, [there is already one](vim.md), but about Neovim and its ecosystem.

## From init.vim to init.lua

Neovim embeds Lua as a first-class citizen to write Vim plugins. This is massively faster than the interpreted VimL. As
a consequence it can also be used for configuring Neovim. These articles helped me to make the transition from VimL
based configuration to lua based configuration. These are three articles that help on the journey:

- [Everything you need to know to configure Neovim using lua](https://vonheikemen.github.io/devlog/tools/configuring-neovim-using-lua/) 
- [From init.vim to init.lua](https://teukka.tech/luanvim.html) 
- [Getting started using Lua in Neovim](https://github.com/nanotee/nvim-lua-guide)

## This & That

### Various Links

[Script to convert snippets from UltiSnips to luasnip](https://github.com/L3MON4D3/LuaSnip/issues/201#issuecomment-950132369)
