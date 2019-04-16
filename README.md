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
sudo apt update
sudo apt install terminator
```

If there is a No release file error, go to **Software & Updates -> Other Software** and uncheck 2 lines that have the word Terminator in them.

4. Install Atom

(Source: https://flight-manual.atom.io/getting-started/sections/installing-atom/)

```
curl -sL https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
sudo apt update
sudo apt install atom
```

If there is a public key error, see #11, replace the public key in #11 buy the public key shown on terminal

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

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-415 # Use the latest one
```

9. Install R & RStudio on Ubuntu

(Source: https://gist.github.com/mGalarnyk/41c887e921e712baf86fecc507b3afc7#file-rstudioubuntu1604-sh)

10. Install Anaconda with zsh

(Source: https://stackoverflow.com/questions/31615322/zsh-conda-pip-installs-command-not-found)

11. Fix GPG Error

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

(Source: https://chrisjean.com/fix-apt-get-update-the-following-signatures-couldnt-be-verified-because-the-public-key-is-not-available/)

12. Add conda environment to Jupyter Lab

(Source: https://stackoverflow.com/questions/53004311/how-to-add-conda-environment-to-jupyter-lab)

```
$ conda activate cenv
(cenv)$ conda install ipykernel
(cenv)$ ipython kernel install --user --name=<any_name_for_kernel>
(cenv($ conda deactivate
```

13. Move /home to a new partition

(source: https://help.ubuntu.com/community/Partitioning/Home/Moving)

14. Solve BIOS and UEFI incompatibility

(Source: http://www.rodsbooks.com/refind/)

Install rEFInd

15. Install Vietnamese keyboard

(Source: https://vinasupport.com/huong-dan-cai-bo-go-tieng-viet-ibus-unikey-tren-ubuntu/)

Use `ibus-ubuntu`

16. Fix `error: unknown filesystem` while installing Arch Linux

(Source: https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)

17. Auto-intall all Atom packages

(Source: https://discuss.atom.io/t/installed-packages-list-into-single-file/12227/2)

```
apm list --installed --bare > package-list.txt
apm install --packages-file package-list.txt
```

18. Fix "Unable to lock the administration directory"

(Source: https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

```
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```
