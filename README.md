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

Update 2020/06/02 for Ubuntu 20.10: Need to upgrade graphic drivers

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

Update 2020/06/02 for Ubuntu 20.10 (https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

```console
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```

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
sudo rm /var/lib/dpkg/lock*
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
alias snap_update="sudo snap refresh"
alias update="sudo apt update -y"
alias upgrade="sudo apt full-upgrade -y"
alias dist="sudo apt dist-upgrade -y"
alias autorm="sudo apt autoremove -y"
alias autoclean="sudo apt autoclean"
alias conda_update="conda update -n base conda -y; conda update --all -y"

alias maintain="snap_update; update; upgrade; dist; autorm; autoclean; conda_update"
```

41. [Install Ubuntu from Windows without a USB](https://askubuntu.com/questions/484434/how-can-i-install-ubuntu-without-cd-and-usb?fbclid=IwAR3LgsSCuD-b3rXTe65qf6rf9Y2hjCk_sDFinJ-FlbvJNsDy3BfnB0bZIHY)

It's a nightmare. Not sure which one works.

42. Atom: [Linter] Error running clang: Failed to spawn command clang

Must install `clang`:

```console
sudo apt install clang
```

43. [Open an mp4 video](https://stackoverflow.com/questions/40760864/how-to-play-mp4-video-in-firefox/40784948)

```console
sudo apt-get install ubuntu-restricted-extras
```

44. [Set `JAVA_HOME`](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04)

```console
sudo nano /etc/environment
```

Then

```console
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
```

45. [Debug slow `zsh`](https://unix.stackexchange.com/questions/565905/oh-my-zshs-prompt-is-slow-how-to-fix-this)

Run the command `set -x` to see which library causes the slowness. Run `set +x` to turn it off

46. [Make `zsh`'s git module run faster](https://stackoverflow.com/questions/12765344/oh-my-zsh-slow-but-only-for-certain-git-repo)

```console
git config --add oh-my-zsh.hide-status 1
git config --add oh-my-zsh.hide-dirty 1
```

47. [Terminator's Ctrl+Shift+E not working in Bionic](https://bugs.launchpad.net/ubuntu/+source/terminator/+bug/1738500)

* launch ibus-setup,
* select emoji tab,
* change the shortcut or remove it

48. [Find package location installed by `apt`](https://askubuntu.com/questions/129022/determine-destination-location-of-apt-get-install-package)

```console
dpkg -L <package>
```

49. Find public IP using command line

```console
curl ifconfig.me
```

50. Check if a port is open for an IP/VM/site

```console
telnet <Public IP> <port>
```

51. Unzip multiple files to a folder with the same name (https://askubuntu.com/questions/518370/extract-several-zip-files-each-in-a-new-folder-with-the-same-name-via-ubuntu-t)

The flag `-n` is used to unzip only non existed files (https://askubuntu.com/questions/994731/how-to-skip-unzipping-a-file-that-already-exists)

```console
find . -name '*.kmz' -exec sh -c 'unzip -n -d "${1%.*}" "$1"' _ {} \;
```

52. Remove a file from a Git repository without deleting it from the local filesystem (https://stackoverflow.com/questions/1143796/remove-a-file-from-a-git-repository-without-deleting-it-from-the-local-filesyste)

```console
git rm --cached mylogfile.log
```

53. Fix a corrupt zsh history file (https://shapeshed.com/zsh-corrupt-history-file/)

```console
mv ~/.zsh_history ~/.zsh_history_bad
strings -eS ~/.zsh_history_bad > ~/.zsh_history
fc -R ~/.zsh_history
rm ~/.zsh_history_bad
```
