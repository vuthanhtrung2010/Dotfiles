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
hyprsunset
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
pavucontrol
```

For `vnstat` setup, after installation, run:
```bash
sudo systemctl enable --now vnstat
```

## ⚙️ Post Installation
### Git Configuration
For github credential strong, use GNome Keyring + libsecret:
```bash
git config --global credential.helper /usr/lib/git-core/git-credential-libsecret
```

### Oh My Zsh + Powerlevel10k + Zsh Plugins
Install Oh My Zsh by following the command in their official website: https://ohmyz.sh/#install

Use powerlevel10k/powerlevel10k for zsh theme
See https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#oh-my-zsh for installation instructions

Also for zsh-autosuggestions, to install do:
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Open `~/.zshrc` and add `zsh-autosuggestions` to the plugins list (find where `plugins=(...)` is located).

Same for zsh-syntax-highlighting:
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
Then add `zsh-syntax-highlighting` to the plugins list in `~/.zshrc`.

## Notes
- For fcitx5 sometimes it can't use Windows + Space toggle language, you can fix it by uncomment the binding SUPER + Space in the hyprland config file.
- For Flameshot fractional scaling issue, you can fix it by uncommenting the line that sets QT_SCALE_FACTOR on hyprland config file.

## Optional Dependencies
```
obs-studio
v4l2loopback-dkms
termius
warp-cli
tailscale
thunderbird
```

For `warp-cli` setup, after installation, run:
```bash
sudo systemctl enable --now warp-svc
```

Then register your device:
```bash
warp-cli register <team-name>
```

`<team-name>` can be found in your warp dashboard. It is optional to include in for network routing.

# Fractional Scaling issue:
- Flameshot: Already tell the solution on above note.
- JetBrains IDEs: Go to `Help > Edit Custom VM Options` append to the opened VM Options file the content below and restart the IDE:
```
-Dawt.toolkit.name=WLToolkit
```

## Secure boot setup
This guide is for `systemd-boot`.

To prevent some tampering we use secure boot on Arch, it was pretty easy, you can use your own key.

1. Enable advanced mode on BIOS
2. Boot Configuration -> Expert Key Management -> Custom Mode -> **Enable**
3. Scroll down and click "Delete all Keys" -> Confirm.
4. Enable Secure boot above if not enabled.
5. Reboot

```bash
# Install sbctl (if you not installed it)
sudo pacman -S --needed sbctl

# Create your keys
sudo sbctl create-keys

# Check status
sudo sbctl status

# Enroll your keys (the -m flag keeps Microsoft keys you enabled)
sudo sbctl enroll-keys -m

# Sign your systemd-boot files
sudo sbctl sign -s -o /usr/lib/systemd/boot/efi/systemd-bootx64.efi.signed /usr/lib/systemd/boot/efi/systemd-bootx64.efi
sudo sbctl sign -s /boot/vmlinuz-linux

# Verify everything
sudo sbctl verify
# Make sure nothing shows as "✗ Not Signed" if has then sign it.
```

Reboot to test again.