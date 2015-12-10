title: Get an app apk from and android device
updated: 2013-07-15 00:00:00
description: 
os: [macosx, windows, linux]
tags: []
deps: []
contributors: ["http://www.github.com/anschwa"] 

List 3rd party packages on your device.
```
adb shell pm list packages -f -3
```


Now pull the package to your computer.
```
adb pull /data/app/XX.XX.XX.apk
```