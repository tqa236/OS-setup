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
```
