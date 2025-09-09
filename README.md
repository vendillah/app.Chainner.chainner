# app.Chainner.chainner

This repository contains an attempt to build and run Chainner using flatpak. This is largely a copy-paste from Element's. I lack Electron (and some flatpak) expertise to understand what is going wrong and what the issue is exactly.

Below you can find how to reproduce the flatpak setup. I ignored the metainfo and borrowed [Element's app icon](https://github.com/flathub/im.riot.Riot/blob/master/ElementLogomark.svg).

```
git clone https://github.com/vendillah/app.Chainner.chainner.git
cd app.Chainner.chainner
```

Next, run the following commands. The first one is to setup flatpak build tools, the third is to build the package using this repository's manifest. The fourth one is to run the app.
```
flatpak install -y flathub org.flatpak.Builder
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak run --command=flathub-build org.flatpak.Builder --install app.Chainner.chainner.yaml
flatpak run app.Chainner.chainner
```

Possible output for the fourth command:

```
[3:0909/202458.562579:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
[3:0909/202458.911076:ERROR:process_singleton_posix.cc(338)] Failed to create /app/Chainner/SingletonLock: Read-only file system (30)
20:24:58.913 › Cleaning up temp folders...
20:24:58.914 › electron-log.transports.file: Can't write to /app/Chainner/logs/main.log Error: ENOENT: no such file or directory, mkdir '/app/Chainner/logs'
    at Object.mkdirSync (node:fs:1396:3)
    at C.testFileWriting (/app/Chainner/resources/app/.vite/build/main.js:7:14474)
    at C.createFile (/app/Chainner/resources/app/.vite/build/main.js:7:14352)
    at C.provide (/app/Chainner/resources/app/.vite/build/main.js:7:14133)
    at k (/app/Chainner/resources/app/.vite/build/main.js:7:16166)
    at F (/app/Chainner/resources/app/.vite/build/main.js:7:15436)
    at g.processMessage (/app/Chainner/resources/app/.vite/build/main.js:1:5953)
    at g.logData (/app/Chainner/resources/app/.vite/build/main.js:1:5386)
    at <computed> [as info] (/app/Chainner/resources/app/.vite/build/main.js:1:4708)
    at Object.log (/app/Chainner/resources/app/.vite/build/main.js:1128:922)
Gtk-Message: 20:24:58.944: Failed to load module "canberra-gtk-module"
Gtk-Message: 20:24:58.944: Failed to load module "canberra-gtk-module"
[3:0909/202458.952490:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
[3:0909/202458.952533:ERROR:bus.cc(399)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
20:24:58.961 › Error: EROFS: read-only file system, open '/app/Chainner/electron-log-preload.js'
    at Object.openSync (node:fs:601:3)
    at Object.func [as openSync] (node:electron/js2c/asar_bundle:2:1869)
    at Object.writeFileSync (node:fs:2249:35)
    at I (/app/Chainner/resources/app/.vite/build/main.js:7:9)
    at App.<anonymous> (/app/Chainner/resources/app/.vite/build/main.js:1:17615)
    at Object.onceWrapper (node:events:628:26)
    at App.emit (node:events:513:28)
```

You can find a few explanations for the current commands in the manifest file.
