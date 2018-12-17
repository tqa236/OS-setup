# setup_ubuntu
Process to set up Ubuntu environment for personal laptop.

1. Fix Time Differences in Ubuntu 16.04 & Windows 10 Dual Boot
(Source: http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)

```timedatectl set-local-rtc 1 --adjust-system-clock```

2. Set the grub default boot entry to remember last choice
(Source: https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice)

Put the following in ```/etc/default/grub```:

```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

Then run:

```sudo update-grub```
