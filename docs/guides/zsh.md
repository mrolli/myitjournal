# Zsh

I finally switched from Bash to Zsh too on my desktop machines. You can consult
my configuration in my [dotfiles](https://github.com/mrolli/dotfiles/tree/main/config/zsh).

## Various Articles Worth Reading

- [A Guide to the Zsh Completion with Examples](https://thevaluable.dev/zsh-completion-guide-examples/)
- [How to profile your zsh startup time](https://esham.io/2018/02/zsh-profiling)

## Using colors in Scripts

Zsh provides a [module](https://github.com/zsh-users/zsh/blob/master/Functions/Misc/colors)
one load that sets up some variables to use to style your terminal output. Load
the module with

    autoload -Uz colors && colors

This defines the following arrays:

- `color` and `colour` with a lot of associations between words and ANSI codes
- `$fg`, `$fg_bold` and `$fg_no_bold` for foreground color sequences
- `$bg`, `$bg_bold` and `$bg_no_bold` for background color sequences

Some examples:

- `$color[31]` has value `red` while `$color[red]` has value `31`
- The `$fg[red]` has emits an escape sequence to change foreground color to red
- The `$bg[blue]` has emits an escape sequence to change background color to
  blue
- `$reset_color` does a color reset

The fg\* and bg\* arrays contain the following colors:

- black
- blue
- cyan
- default
- gray
- green
- grey
- magenta
- red
- white
- yellow

Based on [this blog post](https://www.rockhoppertech.com/blog/zsh-using-color/)
