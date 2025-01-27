# Arch Post-installation process

### Pacman keyring update

```
sudo pacman-key --init
sudo pacman-key --populate archlinux
sudo pacman-key --refresh-keys
sudo pacman -Sy archlinux-keyring
```

### Enabling multilib repo (if needed)

```sudo nvim /etc/pacman.conf```

and then uncomment this section:

```
#[multilib]
#Include = /etc/pacman.d/mirrorlist
```

### Installing a packages for mount/unmount archive/unarchive different types of formats and file systems

```sudo pacman -S lrzip unrar unzip unace p7zip```

and optionally you can install a GUI utility for opening archives

```sudo pacman -S file-roller```

### Enabling Systemd-Oomd Daemon

```sudo systemctl enable --now systemd-oomd```

### Installing Pipewire sound system

```sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack```

and then

```systemctl --user enable --now pipewire.socket pipewire-pulse.socket wireplumber```

optionally you can install rt daemon to decrease a sound lattency
```sudo pacman -S realtime-privileges rtkit```

```sudo usermod -aG realtime "$USER"```
