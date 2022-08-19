# manjaro-i3wm-post-install-guide
packages to install after a fresh manjaro i3 install

Update pacman mirrors
sudo pacman-mirrors -f 30

update installed packages
sudo pacman -Syu

install brave browser
sudo pacman -S brave-browser

Install fish
yay -S fish

enable fstrim to make the SSD happy
sudo systemctl status fstrim.timer
sudo systemctl enable fstrim.timer

sudo ufw enable
sudo systemctl status ufw
sudo systemctl enable ufw

install vscode
yay -S visual-studio-code-bin

Run i3-config-wizard
i3-config-wizard

install alacritty
sudo pacman -S alacritty
Remember to alter default terminal (super+enter) in .i3/config

Install Rofi as an alternative to dmenu
yay -S rofi

Create rofi config by dumping default
rofi -dump-config > ~/.config/rofi/config.rasi
Choose a rofi theme you like
rofi-theme-selector

install neovim and add python support
sudo pacman -S neovim python-neovim

install polybar
sudo pacman -S polybar

install pyenv
sudo pacman -S pyenv
Follow guide here for bash and fish:
https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv

Install poetry, follow guide:
https://python-poetry.org/docs/master/#installing-with-the-official-installer
(Optional) Enable completions for poetry, follow this guide:
https://python-poetry.org/docs/master/#enable-tab-completion-for-bash-fish-or-zsh
