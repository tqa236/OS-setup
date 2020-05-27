# Tips and tricks

* Find wifi password

```bash
security find-generic-password -ga "<WIFI NAME>"
```

* Type square brackets on Azerty keyboard

`Option` + `Shift` + `(` or `)`

* Type e dans l'o on Azerty keyboard

`Option` + `o`

* [Unzip a file with exotic characters](https://github.com/CocoaPods/CocoaPods/issues/7711)

```bash
ditto -V -x -k --sequesterRsrc --rsrc FILENAME.ZIP DESTINATIONDIRECTORY
```

* Unzip all files in a folder

```bash
unzip \*.zip
```

* Update OS and packages with terminal


```bash
softwareupdate -l
softwareupdate -i -a
brew update
brew upgrade
```
