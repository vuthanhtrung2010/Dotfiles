[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetbrainsMono+Nerd+Font&weight=600&size=35&duration=2000&pause=2000&color=F7F7F7&width=435&lines=Trung's+Dotfiles)](https://git.io/typing-svg)
### This repository contains **all of my personal dotfiles**

## 📦 Included Configurations
This repository includes configuration for:
- **Window Managers**: `Hyprland`
- **Terminal**: `kitty` + `fish`
- **Editors**: `VSCode`
- **Status Bar**: `waybar`
- **Notifications**: `mako`
- **Launcher**: `rofi` + `ulauncher`
- **Lockscreen**: `hyprlock`

```plaintext
.
├── akari           # My custom scripts
├── code-flags.conf # VSCode custom flags (for wayland support)
├── hypr
├── LICENSE         # Project LICENSE
├── README.md       # This file
└── waybar
```

## 🚀 Installation
Before installing those dependencies, you should remove default things like dolphin that come with default arch hyprland setup... then install dependencies in the list below.

Needed dependencies:
```
xdg-desktop-portal
xdg-desktop-portal-gnome
xdg-desktop-portal-hyprland
mako
hyprlock
hypridle
hyprpaper
hyprland-monitor-attached
discord
fcitx5
fcitx5-configtool
fcitx5-unikey
flameshot
ulauncher
rofi
nautilus
waybar
brightnessctl
ttf-segoe-ui-variable
ttf-jetbrains-mono-nerd
otf-font-awesome
ttf-font-awesome
noto-fonts-emoji
gnome-keyring
libsecret
wl-clipboard
clipvault
vnstat
ttf-meslo-nerd-font-powerlevel10k
zsh
```

## ⚙️ Post Installation
Use powerlevel10k/powerlevel10k for zsh theme
See https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#oh-my-zsh for installation instructions

For github credential strong, use GNome Keyring + libsecret:
```bash
git config --global credential.helper /usr/lib/git-core/git-credential-libsecret
```

## Notes
- For fcitx5 sometimes it can't use Windows + Space toggle language, you can fix it by uncomment the binding SUPER + Space in the hyprland config file.
- For flameshot fractional scaling issue, you can fix it by uncommenting the line that sets QT_SCALE_FACTOR on hyprland config file.