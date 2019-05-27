## Arch Linux configuration

1. Install Arch Linux

(Source: https://www.ostechnix.com/install-arch-linux-latest-version/)

2. Connect to wifi

(Source: https://growworkinghard.altervista.org/netctl-service-failed/)

3. Install a Desktop environment

(Source: https://wiki.archlinux.org/index.php/xfce)

Install:

```
pacman -S xfce4
pacman -S xfce4-goodies
```

Start: Add `exec startxfce4` to `/etc/X11/xinit/xinitrc`
