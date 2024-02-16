# manjaro i3wm-post-install-guide
Rough guide of packages and apps to install after a fresh manjaro i3 install. Updating as I go through my own setup. 

See also:
- https://jasoneckert.github.io/myblog/configuring-i3/
- https://aptrinh.js.org/manjaro-rice.html

## system

Update pacman mirrors
```
sudo pacman-mirrors -f 30
```

update installed packages
```
sudo pacman -Syu
```

enable fstrim to make the SSD happy. See [this post](https://forum.manjaro.org/t/do-i-need-to-enable-trim-on-m2-ssd/72887/2) for more info

```
sudo systemctl status fstrim.timer
sudo systemctl enable fstrim.timer
```

Change [swappiness](https://wiki.archlinux.org/title/Swap#Swappiness)

Check current swappiness:
```
sysctl vm.swappiness
or
cat /proc/sys/vm/swappiness
```

set permanent swappiness
```
sudo vim /etc/sysctl.d/99-swappiness.conf
vm.swappiness=10
```

Enable [ufw](https://wiki.archlinux.org/title/Uncomplicated_Firewall)
```
sudo ufw enable
sudo systemctl status ufw
sudo systemctl enable ufw
```

Install [fish](https://fishshell.com/)

```
yay -S fish
```

set fish as [default shell](https://github.com/fish-shell/fish-shell#switching-to-fish)
```
chsh -s /usr/local/bin/fish
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

#### (Optional) Update BIOS/Firmware:
[fwupd](https://fwupd.org/) is quick and easy to use, follow the guide on [archlinux wiki](https://wiki.archlinux.org/title/Fwupd)


#### (Optional) Screen flickering issues
First thing to try is to disable Intel's Panel Self Refresh (psr)
See [this](https://askubuntu.com/a/842991) post for how to do it by updating GRUB parameters. [Arch wiki on same issue](https://wiki.archlinux.org/title/Intel_graphics#Screen_flickering) and more info on [GRUB and changing parameters](https://wiki.archlinux.org/title/Kernel_parameters#GRUB)

You can do the same by creating a file `/etc/modprobe.d/`, e.g:
```
sudo nvim /etc/modprobe.d/i915.conf

options i915 enable_psr=0

```

If that doesnt work check if enabling vsync helps.
If you're using picom (default compositor):
```
nvim  ~/.config/picom/picom.conf
vsync = true;
```

## apps

install brave browser (tip: add [ublock origin](https://github.com/gorhill/uBlock) as an extension)

```
sudo pacman -S brave-browser
```
For setting Brave as default browser see [this](https://unix.stackexchange.com/a/434465) post.

install vscode, i prefer the binary to get access to the marketplate

```
yay -S visual-studio-code-bin
```

Install docker, [this guide](https://www.linuxfordevices.com/tutorials/linux/install-docker-on-arch) is quick and simple
## Ricing I3

Install [Rofi](https://wiki.archlinux.org/title/Rofi) as an alternative to dmenu
```
yay -S rofi
```
Create rofi config by dumping default

```
rofi -dump-config > ~/.config/rofi/config.rasi
```
Choose a rofi theme you like by running:
```
rofi-theme-selector
```
(if you're unable to save theme with ALT+a you need to run step above).

Rofi is highly customizeable, e.g. see [this repo](https://github.com/adi1090x/rofi) for a huge collection of custom Applets, Launchers & Powermenus

You can e.g. make the rofi program launcher show icons, my i3 program launcher is:
```
bindsym $mod+d exec --no-startup-id "rofi -show run -show-icons"
```

install [neovim](https://wiki.archlinux.org/title/Neovim) and add python support
```
sudo pacman -S neovim python-neovim
```

install [polybar](https://github.com/polybar/polybar)

```
sudo pacman -S polybar
```
It's wise to install the font-awesome icon pack:

```
sudo pacman -S extra/ttf-font-awesome
```

See the [polybar wiki](https://github.com/polybar/polybar/wiki) for a great intro 

## Python specific
install [pyenv](https://github.com/pyenv/pyenv) to easily switch beteen python versions
```
sudo pacman -S pyenv
```
Follow guide [here](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv) for setting up your shell environment (bash and fish):


Install [poetry](https://python-poetry.org/) to manage packages and dependencies, follow [this guide.](https://python-poetry.org/docs/master/#installing-with-the-official-installer)

(Optional) Enable completions for poetry, follow [this guide](https://python-poetry.org/docs/master/#enable-tab-completion-for-bash-fish-or-zsh)
