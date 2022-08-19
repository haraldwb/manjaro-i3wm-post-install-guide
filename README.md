# manjaro-i3wm-post-install-guide
packages to install after a fresh manjaro i3 install

Update pacman mirrors
```
sudo pacman-mirrors -f 30
```

update installed packages
```
sudo pacman -Syu
```

install brave browser
```
sudo pacman -S brave-browser
```
For setting Brave as default browser see [this](https://unix.stackexchange.com/a/434465) post.

Install [fish](https://fishshell.com/)

```
yay -S fish
```

enable fstrim to make the SSD happy. See [this post](https://forum.manjaro.org/t/do-i-need-to-enable-trim-on-m2-ssd/72887/2) for more info

```
sudo systemctl status fstrim.timer
sudo systemctl enable fstrim.timer
```

Enable [ufw](https://wiki.archlinux.org/title/Uncomplicated_Firewall)
```
sudo ufw enable
sudo systemctl status ufw
sudo systemctl enable ufw
```

install vscode

```
yay -S visual-studio-code-bin
```

i3-config-wizard should run at first i3 boot, if not:
```
i3-config-wizard
```

install [alacritty](https://alacritty.org/)
```
sudo pacman -S alacritty
```
Remember to alter default terminal (default `$super+enter`) in .i3/config
Switch out

Install Rofi as an alternative to dmenu
```
yay -S rofi
```
Create rofi config by dumping default

```
rofi -dump-config > ~/.config/rofi/config.rasi
```
Choose a rofi theme you like
```
rofi-theme-selector
```

install neovim and add python support
```
sudo pacman -S neovim python-neovim
```

install polybar
```
sudo pacman -S polybar
```


## Python specific
install pyenv
```
sudo pacman -S pyenv
```
Follow guide [here](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv) for setting up your shell environment (bash and fish):


Install poetry, follow [this](https://python-poetry.org/docs/master/#installing-with-the-official-installer) guide:

(Optional) Enable completions for poetry, follow [this](https://python-poetry.org/docs/master/#enable-tab-completion-for-bash-fish-or-zsh) guide:

