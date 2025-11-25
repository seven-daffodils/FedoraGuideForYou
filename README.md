# FedoraGuideForYou

Another Fedora guide for my friends

## RPM Fusion

1. Install [RPM Fusion](https://rpmfusion.org/RPM%20Fusion).

```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## Software

### Brave

You can install [Brave](https://brave.com/linux/) by using the following commands:

```
sudo dnf install dnf-plugins-core
sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
sudo dnf install brave-browser
```

### Tor

```
sudo dnf install torbrowser-launcher
```

### Signal

```
# Install distrobox and create a Ubuntu container
sudo dnf install -y distrobox
distrobox-create -i ubuntu:latest -n ubuntu -Y

# Install Signal and libasound2t64 inside the container and export the app
distrobox-enter -n ubuntu -- bash -c '

        # 1. Install our official public software signing key:
        wget -O- https://updates.signal.org/desktop/apt/keys.asc | gpg --dearmor > signal-desktop-keyring.gpg;
        cat signal-desktop-keyring.gpg | sudo tee /usr/share/keyrings/signal-desktop-keyring.gpg > /dev/null

        # 2. Add our repository to your list of repositories:
        wget -O signal-desktop.sources https://updates.signal.org/static/desktop/apt/signal-desktop.sources;
        cat signal-desktop.sources | sudo tee /etc/apt/sources.list.d/signal-desktop.sources > /dev/null

        # 3. Update your package database and install Signal:
        sudo apt update && sudo apt install -y signal-desktop libasound2t64

# Export the app
distrobox-export -a signal-desktop -ef --disable-gpu
'

# Rename the desktop file so that the upper-left icon works correctly on KDE
mv ~/.local/share/applications/ubuntu-signal-desktop.desktop ~/.local/share/applications/signal.desktop
```

## Multimedia

See [this guide](https://rpmfusion.org/Howto/Multimedia?highlight=%28%5CbCategoryHowto%5Cb%29).

Install full ffmpeg from RPM Fusion

```
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
```

### Hardware accelerated codec

```
sudo dnf install inter-media-driver
```

```
sudo dnf install libva-intel-driver
```

### Appearance

#### Installing Papirus icon theme

`sudo dnf install -y papirus-icon-theme`

#### Installing cursors

##### Banana cursor (thanks to [ful1e5](https://github.com/ful1e5))

```
wget https://github.com/ful1e5/banana-cursor/releases/download/v2.0.0/banana-all.tar.xz
mkdir -p ~/.icons/
tar -xvf banana-all.tar.xz -C ~/.icons/ && rm banana-all.tar.xz
```

##### Google dot cursor (thanks to [ful1e5](https://github.com/ful1e5))

```
wget https://github.com/ful1e5/Google_Cursor/releases/download/v2.0.0/GoogleDot-{Black,Blue,Red,White}.tar.gz
mkdir -p ~/.icons/
for file in GoogleDot-*.tar.gz; do tar -xvf "$file" -C ~/.icons/ && rm "$file"; done
```

##### Bibata cursor (thanks to [ful1e5](https://github.com/ful1e5))

```
wget https://github.com/ful1e5/Bibata_Cursor/releases/download/v2.0.7/Bibata.tar.xz
mkdir -p ~/.icons/
tar -xvf Bibata.tar.xz -C ~/.icons/ && rm Bibata.tar.xz
```
