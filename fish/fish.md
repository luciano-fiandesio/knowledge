# Fish

[Fish](https://fishshell.com) is the shell I use both on my MacBook Pro and on my Ubuntu dektop.
It offers a number of useful feature which are not available in Bash, such as :

- searchable command history
- tab completion using man-page data
- scripting 
- aliases and abbreviations
- Web-based configuration

It works mostly out of the box, since the defaults are very well thought out.

## Installation

### OSX

`brew install fish`

add `/usr/local/bin/fish` at the end of the file `/etc/shells`

Change the default shell to fish:

`chsh -s /usr/local/bin/fish`

### Ubuntu

```
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt-get update
sudo apt-get install fish

# check where is the fish executable
whereis fish

chsh -s /usr/bin/fish

# check that fish shell is added into /etc/shells file or not. If not:

echo /usr/bin/fish | sudo tee -a /etc/shells
```

## Package managers

- [Fisher](https://github.com/jorgebucaran/fisher) - Minimal, fast and reliable package manager.

## Commands, utilities, functions

- [z](https://github.com/jethrokuan/z) - Pure-fish [rupa/z](https://github.com/rupa/z)-like directory jumping.
- [bass](https://github.com/edc/bass) - Run bash scripts, replaying environment changes in fish
- [fzf](https://github.com/jethrokuan/fzf) - Improved key bindings for [junegunn/fzf](https://github.com/junegunn/fzf)
- [brew-completions](https://github.com/laughedelic/brew-completions) - Fish shell completions for Homebrew
- [sdkman](https://github.com/reitzig/sdkman-for-fish) - Makes command `sdk` from [SDKMAN!](https://github.com/sdkman/sdkman-cli) available in fish
- [update](https://github.com/publicarray/update) - Updates OS and packages

## Themes

- [Starship](https://github.com/starship/starship)

## Tools

### [fzf](https://github.com/junegunn/fzf) integration

`CTRL+T` show files and folders
`CTRL+R` show history
`ALT+C` `cd` into directory
`ALT+o` open a file using default editor (`$EDITOR`)