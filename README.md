# Ubuntu configuration
Process to set up Ubuntu environment for personal laptop.

1. Fix Time Differences in Ubuntu 16.04 & Windows 10 Dual Boot

(Source: http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)

```
timedatectl set-local-rtc 1 --adjust-system-clock
```

2. Set the grub default boot entry to remember last choice

(Source: https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice)

Put the following in ```/etc/default/grub```:

```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

Then run:

```
sudo update-grub
```

3. Install terminator

(Source: https://gnometerminator.blogspot.com/p/introduction.html)

```
sudo add-apt-repository ppa:gnome-terminator
sudo apt-get update
sudo apt-get install terminator
```

4. Install Atom

(Source: https://flight-manual.atom.io/getting-started/sections/installing-atom/)

```
curl -sL https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
sudo apt-get update
```

Python packages: atom-beautify, autocomplete-python, compare-files, docblock-python, linter, linter-flake8, linter-pydocstyle, pretty-json, python-autopep8, python-tools, python-yapf, script, linter-mypy, linter-pylint

C++ packages: atom-ctags, atomic-rtags, autocomplete-ctags, linter-clang, atom-terminal-panel, switch-header-source

5. Configure Firefox

- Restore previous section
- Always ask you where to save files
- Install Adblock Plus and EverSync

6. Ubuntu hangs on boot

(Source: https://askubuntu.com/questions/764568/ubuntu-16-04-hangs-on-shutdown-restart)

7. Ubuntu 16.04 freezes on restart

(Source: http://michalorman.com/2013/10/fix-ubuntu-freeze-during-restart/)

Put the following in ```/etc/default/grub```:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
```

Then run:

```
sudo update-grub
```

8. Update graphical card drivers for Ubuntu
(Source: https://www.howtogeek.com/242045/how-to-get-the-latest-nvidia-amd-or-intel-graphics-drivers-on-ubuntu/)
