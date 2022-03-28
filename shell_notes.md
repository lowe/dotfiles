# Recommended zsh + vim setup for MacOS and Linux.
Use `brew` on MacOS, and `apt`/`pacman`/`yum` etc on Linux.

## iTerm2
- 1a. No iTerm2? Install `https://iterm2.com/`
- 1b. Already installed iTerm2? Then, what specific customization did you make?

2. Confirm your default shell is `zsh`.

```
whoami
pwd
cd

# print info about currently running shell process.
# see:
# https://www.cyberciti.biz/tips/how-do-i-find-out-what-shell-im-using.html
ps -p $$

# print what the SHELL environment variable is set to.
echo $SHELL

# interactive command for changing login shell.
chsh

which zsh
zsh --version
```

3.
go to: iTerm2 menu > Preferences...

#### Click on `Profiles` tab, `General` subtab:
see what "Command" dropdown is set to. If "Login shell", then it will defer to whatever your login shell is set to, which you can change via `chsh` aka "change shell" command. If you have trouble making iTerm2 use zsh instead of bash, this dropdown is an easy way to fix: you can directly type the shell command to run, eg: `/usr/local/bin/zsh`, instead of defaulting to login shell.

#### Click on `Profiles` tab, `Colors` subtab:
set `Color Presets...` dropdown to `Solarized Dark`


## other download tools
```
# confirm wget and curl. brew install these if you don't have them.
which wget
which curl
```

## `zsh` setup

```
mv .zshrc{,.old}
# ^ same command as: mv .zshrc .zshrc.old
```

Install oh-my-zsh `https://ohmyz.sh/`

This installation flow will create a new `.zshrc` file for you. You can delete it and use mine instead:

```
# confirm that current ~/.zshrc is new boilerplate
ls -l ~/.zshrc*
cat ~/.zshrc

# now remove it
rm ~/.zshrc

# put my zshrc and vimrc in a '~/dotfiles' directory and make symbolic links
mkdir ~/dotfiles

mv path/to/downloaded_dotzshrc ~/dotfiles/dotzshrc
mv path/to/downloaded_dotvimrc ~/dotfiles/dotvimrc

ln -s ~/dotfiles/dotzshrc ~/.zshrc
ln -s ~/dotfiles/dotvimrc ~/.vimrc
```

Lastly, a few more dependencies for my zsh setup:

```
# see: https://github.com/zsh-users/zsh-syntax-highlighting
brew install zsh-syntax-highlighting

# see: https://github.com/sindresorhus/pure
mkdir -p "$HOME/.zsh"
git clone https://github.com/sindresorhus/pure.git "$HOME/.zsh/pure"
```

## `brew` and `vim`
```
brew install vim
```

## vim: install `vim-plug`

https://github.com/junegunn/vim-plug

Follow install instructions under "Vim / Unix" subsection. It will consist of a `curl` command that adds a `plug.vim` file in your vim plugin autoload directory.

Confirm that it worked:
```
less ~/.vim/autoload/plug.vim
```

Open vim. Ignore any errors:
```
vim
```

Inside vim, run `:PlugInstall` from the vim command line. It should correctly install a bunch of vim plugins. Now quit vim: `:q`
Reopening `vim` from the command line, confirm that it launches without errors.

## `fd` and `ripgrep`

https://github.com/sharkdp/fd
https://github.com/BurntSushi/ripgrep

```
brew install fd
brew install ripgrep
```


## Shell commands to learn

tab between applications:
`command-tab` and `command-shift-tab`

tab between windows within an application:
`command-backtick` and `command-shift-backtick`

search command history incrementally: backwards / forwards
`ctrl+r` and `ctrl+s`

go to beginning / end of command line
`ctrl+a` and `ctrl+e`

start current command over again:
`ctrl+u`

clear the screen but keep the command i've written so far:
`ctrl+l`
(this keyboard shortcut does the same thing as the `clear` command)


## vim commands to learn

```
cd somewhere/inside/a/git/repo
vim
```

So far, you're inside a big repo, opened vim, but haven't said which file to edit. Now press:
`ctrl+p`
and do an incremental path search. Opening / changing files this way is like using Spotlight (Command-space) on MacOS, and much faster than manually entering long paths, even with help from tab completion.

Now that you're editing a file...
press `i` to enter insert mode
type the first letter of a variable
type `ctrl+p`

- `ctrl+p` does autocompletion when you're typing stuff (insert mode)
- `ctrl+p` does an incremental search to help jump to a file otherwise (command mode)

Other commands:
```
# quit
:q

# force quit (discard changes)
:q!

# write file then quit
:wq

# edit a new path
# (using ctrl+p is usually faster)
:e

# previous buffer
:bp

# next buffer
:bn
```
