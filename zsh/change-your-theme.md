# Themes
Omz is a plugin engine and as such comes bundled with loads of themes you can use to change the prompt. 

In order to enable a theme, set `ZSH_THEME` to the name of the theme in your `~/.zshrc` , before sourcing Oh My Zsh; for example: `ZSH_THEME="af-magic"` . If you do not want any theme enabled, just set `ZSH_THEME`  to blank: `ZSH_THEME=""` 

The prompt is the line (or lines, on multiline themes) that appear every time you want to run a command. This is ultimately accomplished by changing the $PROMPT variable. But a theme can do much more than that, like adding an automatic git status prompt that changes each time the prompt is redrawn, or a clock that is refreshed per-second, or many other functionalities like that. 

A zsh theme can't change the appearance of your terminal emulator. This includes things like the color scheme or the character font. Those are separate settings that need to be configured in your terminal emulator settings. 

This is done in iTerm2 by going Profiles > Open Profiles > Edit Profiles > Colors. 

[source](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) 
