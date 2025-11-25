# FedoraGuideForYou

Another Fedora guide for my friends

## RPM Fusion

1. Install [RPM Fusion](https://rpmfusion.org/RPM%20Fusion).

```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## Browsers

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

```
# A banana cursor (thanks to ful1e5)

wget https://github.com/ful1e5/banana-cursor/releases/download/v2.0.0/Banana.tar.xz
```
