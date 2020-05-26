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

```console
sudo update-grub
```

3. Install terminator

```console
sudo apt update
sudo apt install terminator
```

If there is a No release file error, go to **Software & Updates -> Other Software** and uncheck 2 lines that have the word Terminator in them.

4. Install Atom

Update (02/02/2020)

```console
sudo snap install atom --classic
```

(Source: https://flight-manual.atom.io/getting-started/sections/installing-atom/)

```console
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

```console
$ sudo update-grub
```

8. Update graphical card drivers for Ubuntu

(Source: https://www.howtogeek.com/242045/how-to-get-the-latest-nvidia-amd-or-intel-graphics-drivers-on-ubuntu/)

```console
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-415 # Use the latest one
```

9. Install R & RStudio on Ubuntu

(Source: https://gist.github.com/mGalarnyk/41c887e921e712baf86fecc507b3afc7#file-rstudioubuntu1604-sh)

10. Install Anaconda with zsh

(Source: https://stackoverflow.com/questions/31615322/zsh-conda-pip-installs-command-not-found)

11. Fix GPG Error

```console
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

(Source: https://chrisjean.com/fix-apt-get-update-the-following-signatures-couldnt-be-verified-because-the-public-key-is-not-available/)

12. Add conda environment to Jupyter Lab

(Source: https://stackoverflow.com/questions/53004311/how-to-add-conda-environment-to-jupyter-lab)

```console
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

```console
apm list --installed --bare > package-list.txt
apm install --packages-file package-list.txt
```

18. Fix "Unable to lock the administration directory"

(Source: https://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

```console
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```

19. Recursively find all files with a given name

```console
find . -name "foo*"
```

20. The difference between `$` and `#` in command line commands?

(Source: https://stackoverflow.com/questions/35104339/what-does-the-mean-in-command-line-commands/48215530#48215530)

`$` is there to tell you that this command needs to be executed as a regular user. `#` commands must be executed as **root**

21. [Check for large softwares](https://www.commandlinefu.com/commands/view/3842/list-your-largest-installed-packages-on-debianubuntu)

```console
# sudo apt install wajig
wajig large
```

22. [Delete all remote branches except master on Git](https://www.hacksparrow.com/git/delete-all-remote-branches-except-master.html)

```console
git branch -r |  grep "^  ${REMOTE}/" | sed "s|^  ${REMOTE}/|:|" | grep -v "^:HEAD" | grep -v "^:${MASTER}$" | xargs git push ${REMOTE}
```

23. [Create ssh config file to connect to a remote server](https://linuxize.com/post/using-the-ssh-config-file/)

```console
touch ~/.ssh/config
chmod 600 ~/.ssh/config
```

24. [ssh connect without password](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/)

```console
ssh-copy-id remote_username@server_ip_address
```

25. Share keyboard and mouse between multiple computers

(Souce: https://askubuntu.com/questions/1064465/free-software-to-share-mouse-and-keyboard-between-linux-and-windows)

For now, only work if Ubuntu is a server and Windows is a client

26. Install zsh plugins

* autosuggestions: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md
* command not found: https://askubuntu.com/questions/34978/configuring-to-detect-if-a-command-does-not-exist-suggest-installation

```console
[[ -a "/etc/zsh_command_not_found" ]] && . /etc/zsh_command_not_found
```

27. Sort directories by size

```console
du -h --max-depth=1 | sort -hr
```

28. [cannot create temp file for here-document: No space left on device](https://unix.stackexchange.com/questions/277387/tab-completion-errors-bash-cannot-create-temp-file-for-here-document-no-space)

Use this command to find the big files, then delete only the big files.

```console
du -hs /tmp /var/log 
```

29. [Delete caches](https://askubuntu.com/questions/102046/is-it-okay-to-delete-the-cache-folder)

This will delete everything in your .cache that was last accessed more than a year ago

```console
find ~/.cache/ -type f -atime +365 -delete
```

If you're nervous about running it, this will show you what's going to be deleted:

```console
find ~/.cache/ -depth -type f -atime +365
```

30. [Find and remove content with `sed`](https://stackoverflow.com/questions/905144/sed-beginner-changing-all-occurrences-in-a-folder)


```console
find . -type f -exec sed -i "s/foo/bar/g" {} \;
```

40. Update all

```
alias update="sudo apt update"
alias upgrade="sudo apt upgrade"
alias dist="sudo apt dist-upgrade"
alias autorm="sudo apt autoremove"
alias autoclean="sudo apt autoclean"

alias maintain="update; upgrade; dist; autorm; autoclean"
```

41. [Install Ubuntu from Windows without a USB](https://askubuntu.com/questions/484434/how-can-i-install-ubuntu-without-cd-and-usb?fbclid=IwAR3LgsSCuD-b3rXTe65qf6rf9Y2hjCk_sDFinJ-FlbvJNsDy3BfnB0bZIHY)

It's a nightmare. Not sure which one works.
