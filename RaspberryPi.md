# Uncharted water

1. [Connect Raspberry Pi to PC using USB C](https://howchoo.com/pi/raspberry-pi-gadget-mode)

Step 1: Flash Raspberry Pi OS onto the SD card

Step 2: Edit config.txt on the boot partition

```
dtoverlay=dwc2
```

Step 3: Enable SSH

```
touch ssh
```

Step 4: In `cmdline.txt`, look for `rootwait`, and add `modules-load=dwc2,g_ether` immediately after, separated by a space.

Example:

```
console=serial0,115200 console=tty1 root=PARTUUID=6c586e13-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait modules-load=dwc2,g_ether quiet init=/usr/lib/raspi-config/init_resize.sh
```
