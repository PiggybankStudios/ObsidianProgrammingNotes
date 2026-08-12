# bin -> usr/bin
---
# boot
Contains files like `initrd.img-6.17.0-5-generic`, `memtest86+x64.bin`, `System.map-6.17.0-5-generic`

---
# dev
Contains a bunch of device "files" like `tty1`, `ttyS2`, `vcs`, `loop0`, `console`, etc.
## dev/block
## dev/bsg
## dev/bus
## dev/char
## dev/cpu
## dev/disk
## dev/dma_heap
## dev/dri
## dev/hugepages
## dev/input
## dev/mapper
## dev/net
## dev/pts
## dev/snd
## dev/vfio

---
# etc
Lots of `.conf` or `.ini` configuration files and subfolders (often subfolders have `.d` suffix). For example `etc/gtk-3.0/settings.ini` contains options like `gtk-theme-name = Yaru`
## etc/init.d/
Contains various executables that startup during initialization? (like `cron`, `dbus`, `sddm`, etc.)
## etc/apt/sources.list.d/
This is where `ubuntu.sources` lives
Sublime Text install has us make a `sublime-text.sources` and `sublime-text.list` here

---
# home
## home/\[username\]/
### home/\[username\]/Desktop
### home/\[username\]/Documents
### home/\[username\]/Downloads
### home/\[username\]/Music
### home/\[username\]/Pictures
### home/\[username\]/Public
### home/\[username\]/Templates
### home/\[username\]/Videos
### home/\[username\]/snap

---
# lib -> usr/lib
---
# lib32 -> usr/lib32
---
# lib64 -> usr/lib64
---
# lost+found
Permission denied

---
# media
Empty, sometimes `cdrom` folder is present by default

---
# mnt
Empty by default. Can mount volumes here

---
# opt
Empty by default

---
# proc
Subfolders for each active process' PID as well as other files like `proc/state`, `proc/uptime`, etc.

---
# root
Permission denied

---
# run
A bunch of subfolders
## run/user
Subfolders for each user ID?

---
# sbin -> usr/sbin
---
# snap
Visit https://forum.snapcraft.io/t/the-snap-directory/2817
`README`:
> This directory represents installed snap packages. `snap/bin` contains symlinks to snap applications

---
# srv
Empty by default

---
# sys
## sys/block
## sys/bus
## sys/class
## sys/dev
## sys/devices
## sys/firmware
## sys/fs
## sys/hypervisor
## sys/kernel
## sys/module
## sys/power

---
# tmp
Seems like all temporary files go here? Often they are named after they use-case rather than fully random names like on Windows

---
# usr
## usr/bin
`chown`, `mount`, etc.
## usr/games (Lubuntu)
`2048-qt` on Lubuntu.
`gamemodelist`, `gamemoderun`, and `gamemode-simulate-game` on Ubuntu.
## usr/include
`stdio.h`, `stdint.h`, etc.
### usr/include/linux
### usr/include/X11
### usr/include/misc
### usr/include/x86_64-linux-gnu
#### usr/include/x86_64-linux-gnu/sys
## usr/lib
Almost entirely subfolders, only a few .so files live a the top level
### usr/lib/X11
### usr/lib/apt
### usr/lib/dbus-1.0
### usr/lib/dpkg
### usr/lib/grub
### usr/lib/init
### usr/lib/kernel
### usr/lib/linux
### usr/lib/nvidia
### usr/lib/pkgconfig
Would hold `.pc` files that could be used when compiling with `pkg-config --cflags [pkg_name]`
### usr/lib/python3
### usr/lib/qt6
### usr/lib/ssl
### usr/lib/x86_64-linux-gnu
## usr/lib32
Folder is not on Lubuntu, exists on Ubuntu
## usr/lib64
`ld-linux-x86-64.so.2` (only file on Lubuntu and Ubuntu)
## usr/libexec
Lots of executables like `xdg-desktop-portal`, `xdg-desktop-portal-gtk`, etc. and a few subfolders
## usr/local
### usr/local/bin
Empty on Lubuntu fresh install
### usr/local/etc
Empty on Lubuntu fresh install
### usr/local/games
Empty on Lubuntu fresh install
### usr/local/include
Empty on Lubuntu fresh install
### usr/local/lib
Empty on Lubuntu fresh install (except for empty `python3.13/dist-packages` folder)
### usr/local/libexec
Empty on Lubuntu fresh install
### usr/local/sbin
Empty on Lubuntu fresh install
### usr/local/share
Empty on Lubuntu fresh install (except for a few empty folders like `ca-certificates`, `fonts`, `man`, etc.)
### usr/local/src
Empty on Lubuntu fresh install
## usr/sbin
Lots of executables like `adduser`, `fdisk`, etc.
## usr/share
Lots of subfolders for various applications like `vlc`, `vim`, `java`, etc. Folders contain resources like `.ico` and `.gresource`
## usr/src
### usr/src/linux-headers-(kernel_version)
### usr/src/linux-headers-(kernel_version)-generic
### usr/src/linux-hwe-(kernel_version)-headers-(kernel_version)

---
# var
## var/backups
## var/cache
## var/crash
## var/lib
## var/local
## var/log
Lots of .log files in here, like `/var/log/apt/history.log` and compressed backups like `/var/log/apt/history.log.1.gz`
Often rotated by `logrotate`. See `/etc/cron.daily/logrotate`, `/etc/logrotate.conf`, and `/etc/logrotate.d/`
`/var/log` is owned by `adm` group?
## var/mail
## var/metrics
## var/opt
## var/snap
## var/spool
## var/tmp
