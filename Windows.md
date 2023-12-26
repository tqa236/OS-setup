# Windows

## (Because even a Linux user need to play game)

* [Change the default path in PowerShell ISE](https://stackoverflow.com/questions/32069265/how-to-set-powershell-default-directory/32069943)

* [Reduce WinSxS size](https://www.windowscentral.com/how-reclaim-space-reducing-size-winsxs-folder-windows-10)

```PowerShell
dism /Online /Cleanup-Image /AnalyzeComponentStore
dism /online /Cleanup-Image /StartComponentCleanup
```

* [Change name by pattern](https://devblogs.microsoft.com/scripting/use-powershell-to-rename-files-in-bulk/)

```PowerShell
Get-ChildItem -Filter “*current*” -Recurse | Rename-Item -NewName {$_.name -replace ‘current’,’old’ }
```

* Turn off the sound popup on Google Chrome

Paste `chrome://flags/#hardware-media-key-handling` to the browser and turn it off.

* Check file size recursively

Use [TreeSize Free](https://www.jam-software.com/treesize_free) (better) or [WinDirStat](https://windirstat.net/)

* [Delete files on System Volume Information](https://www.tenforums.com/general-support/114584-how-do-i-delete-files-system-volume-information.html)

```PowerShell
vssadmin Resize ShadowStorage /For=C: /On=C: /Maxsize=320MB
vssadmin delete shadows /for=c: /all /quiet
```

* Iterate through all subdirectories and format code

```PowerShell
Get-ChildItem -Directory | Foreach-Object {dotnet-format -w $_.FullName}
Get-ChildItem -Directory | Foreach-Object {fantomas $_.FullName}
```

* Remove items with pattern
```PowerShell
Get-ChildItem -Filter "*.txt" -Recurse | Remove-Item
```

* Update PowerShell by the command line (https://superuser.com/questions/1287032/update-powershell-through-command-line)

Stable version

```PowerShell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```

Preview version

```PowerShell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI -Preview"
```

* Shrink WSL file:

Use https://github.com/mikemaccana/compact-wsl2-disk or https://superuser.com/a/1734392

* Run scripts with PowerShell: https://stackoverflow.com/questions/4037939/powershell-says-execution-of-scripts-is-disabled-on-this-system

```PowerShell
powershell -ExecutionPolicy Bypass -File script.ps1
```

* Remove `wsl` volume

```PowerShell
wsl.exe --list --verbose
wsl --unregister <NAME>
```

* No Internet connection in WSL (https://stackoverflow.com/questions/62314789/no-internet-connection-on-wsl-ubuntu-windows-subsystem-for-linux)

Open PowerShell as an Administrator and type these commands:

```PowerShell
netsh winsock reset 
netsh int ip reset all
netsh winhttp reset proxy
ipconfig /flushdns
```

Reboot your machine.
