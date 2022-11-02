# Vim

## Installing Vim

=== "macOS"
    On macOS Vim is also already installed, but it's quite an onld version and
    has no python support built in. Therefore it's suggested to install a recent
    version using Homebrew: `brew install vim`

=== "Linux"

    Every Linux distribution brings a Vim package that is installable by using the distribution's package manager.

Besides Vim also consider to **use Neovim** right away. This is a modern drop-in
replacement for Vim. That means it function almost identical, can almost be
identically configured, but feature Lua support and a lot more possibilities and
features. Neovim can also be installed using Homebrew or from a pre-built
package. See [Neovim releases](https://github.com/neovim/neovim/releases/tag/v0.8.0)
for the download links.

## Tutorials

When beginning the journey of master Vim, a first stop might the built in
tutorial. Type `vimtutor` to start this "interactive document".

There is huge Vim tutorial in 5 pieces targetting beginners and builds up to veterans:

* [Is Vim Really Not For You? A Beginner Guide](https://thevaluable.dev/vim-beginner/)
* [A Vim Guide for Intermediate Users](https://thevaluable.dev/vim-intermediate/)
* [A Vim Guide for Advanced Users](https://thevaluable.dev/vim-advanced/)
* [A Vim Guide for Adept Users](https://thevaluable.dev/vim-adept/)
* [A Vim Guide for Veteran Users](https://thevaluable.dev/vim-veteran/)

And other Tutorials with its strengths and weaknesses:

* [Boost your coding fu](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/table-of-contents)
* [Boost.. Cheatsheet](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/cheatsheet/)
* [Learn Vim Progressively](http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/)

And espcially about Text Objects:

* [Vim Text Objects: The Definitive Guide][vim-text-objects]

And Vimscript which also covers customizing Vim and not only plugin development:

* [Learn Vimscript the Hard Way](https://learnvimscriptthehardway.stevelosh.com/)

And finally one from the Vim project leader Bram Moolenaar himself, though not
for beginners but those that already know Vim for some time but want to get better:

* [Seven habits of effective text editing](https://www.moolenaar.net/habits.html)

There's even a browser game [**vim-adventures**](https://vim-adventures.com/)
that teaches Vim.

## Learning Videos

### The Vim Tutorial (beginner)

[![Part One - Basic Commands](http://img.youtube.com/vi/ER5JYFKkYDg/0.jpg)](https://www.youtube.com/watch?v=ER5JYFKkYDg)
[![Part Two - More Commands](http://img.youtube.com/vi/tExTz7GnpdQ/0.jpg)](https://www.youtube.com/watch?v=tExTz7GnpdQ)

### Mastering the Vim Language (advanced)

[![Mastering the Vim Language](http://img.youtube.com/vi/wlR5gYd6um0/0.jpg)](http://www.youtube.com/watch?v=wlR5gYd6um0/)

### How to Do 90% of What Plugins Do (With Just Vim) (advanced)

[![How to Do 90% of What Plugins Do (With Just Vim)](http://img.youtube.com/vi/XA2WjJbmmoM/0.jpg)](http://www.youtube.com/watch?v=XA2WjJbmmoM/)

## Suggested Plugins

### General Plugins

!!! tip "vim-surround"
    The plugin [tpope/vim-surround](https://github.com/tpope/vim-surround) by
    [Tim Pope](https://github.com/tpope/) feature text objects and commands
    regaring manipulation of surroundings.  
    See the glorious tutoriol of [Daniel Weibel](https://weibeld.net/vim/surround-plugin.html).

!!! tip "vim-indent-object"
    This plugin features new text objects for working on indendet blocks of any
    kind. Found at [vim-text-objects]. For usage see the [docs](https://github.com/michaeljsmith/vim-indent-object)

### Markdown

There's a good write-up on [using markdown in Vim][vim-markdown]

!!! tip "vim-criticmarkup"
    If using ciritic markup, this plugin adds vim functions to approve or reject
    changes, though obviously not maintained anymore. Recommended by [vim-markdown].

Another good blog post is [Markdown Writing and Previewing in Neovim - A Complete
Guide]

[Markdown Writing and Previewing in Neovim - A Complete Guide]: https://jdhao.github.io/2019/01/15/markdown_edit_preview_nvim/
[vim-markdown]: https://vim.works/2019/03/16/using-markdown-in-vim/
[vim-text-objects]: https://blog.carbonfive.com/vim-text-objects-the-definitive-guide/

## Further Readings

[Vim/Nvim useful tricks](https://medium.com/@voyeg3r/vim-nvim-useful-tricks-456efd767240):
Lots of short tips on shortcuts
