## Setup

See [shell_notes.md](shell_notes.md) for setup.

To make inspection easier, these filenames all start with `dot` instead of `.`

One way to add all of the correct dotfile paths, such as `~/.zshrc`, is to clone this repo and add symlinks:
```
shell-prompt$ for f in dotfiles/dot*
do
  ln -si "$f" ~/"$(basename "$f" | sed 's/dot/./')"
done
```
