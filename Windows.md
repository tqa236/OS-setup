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

* Turn off the Media Session Service on Google Chrome

Paste `chrome://flags/#enable-media-session-service` to the browser and turn it off.
