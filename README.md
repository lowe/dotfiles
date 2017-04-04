## Setup

Configure terminal to a [solarized-dark](http://ethanschoonover.com/solarized) color scheme,
(colors might be off otherwise), then:
```
$ git clone --recursive https://github.com/lowe/dotfiles

$ for f in dotfiles/dot*
do
  ln -si "$f" ~/"$(basename "$f" | sed 's/dot/./')"
done
```
