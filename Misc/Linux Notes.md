## Notes
- [ ] To get sokol compiling on Ubuntu WSL we need to install the following packages
	- `mesa-common-dev` (for `GL/gl.h`)
	- `libxi-dev` (for `XInput2.h`)
	- `libxcursor-dev` (for `Xcursor.h`)
- [ ] After compiling a sokol app successfull on WSL I get the following panic on startup:
```cpp
      [sapp][panic][id:48] ../../third_party/sokol/sokol_app.h:11614:0:
        LINUX_X11_OPEN_DISPLAY_FAILED: XOpenDisplay() failed
```
- [ ] `something.a` files are "archive" libraries (aka static library), `libsomething.so` are "shared object libraries" (aka dynamic library)
- [ ] `objdump -p program_name` is super useful for inspecting programs and libraries after they are created to see their dependencies (`grep NEEDED` for example)
- [ ] You can change the shell prompt text by modifying `PS1` environment variable. For example `PS1="\u >>"` will make the prompt simply show as `robbitay >>` (with no coloring, no path, and no `@TaylorsComputer`)
	- [ ] Default value for PS1 can be found in `~/.bashrc`, for me it was `${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ ` when colors are enabled or `${debian_chroot:+($debian_chroot)}\u@\h:\w\$ ` when they are not enabled
	- [ ] For a shorter prompt try `PS1="\[\033[01;32m\]\u \[\033[01;34m\]\W \[\033[00m\]> "` (also can use emoji like ✨ instead of `>`)
	- [ ] Variables that can be used: [Bash Prompt Escape Sequences](https://tldp.org/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html)
		- `\u` = Username
		- `\h` = Computer Name?
		- `\w` = Current Working Directory
- [ ] In a bash script (`.sh` file) you can set an environment variable like so: `VARIBLE_NAME="value"` (NOTE: you must use `"` or `'` around your value)
- [ ] Check which desktop environment is currently running with `echo $DESKTOP_SESSION`
- [ ] Fonts are stored in `/usr/share/fonts` or `~/.local/share/fonts`. You can find a font using `fc-match [font_name]` (optionally pass `--format="%{file}\n"`)
- [ ] List manually installed packages with `apt-mark showmanual`
- [ ] Create a new user with `sudo adduser robbitay`, give a password Full Name, Room Number, Work Phone, Home Phone, and Other. This also creates a group called `robbitay`. Added user to `sudo` group by doing `sudo usermod -aG sudo robbitay`. List groups for a user by doing `groups robbitay`.
	- Alternatively there is a file called `/etc/sudoers` that should be edited **only** with `visudo` to add sudo permissions for users.
- [ ] List logged in users with `w` command (or `who -H`):
```
 22:40:08 up  1:56,  4 users,  load average: 0.06, 0.02, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU  WHAT
root              NN.NNN.NNN.NN    22:37    1:55m  0.00s  0.03s sshd-session: root [priv]
root              -                22:37    1:55m  0.00s  0.20s /usr/lib/systemd/systemd --user
robbitay          NNN.NNN.NNN.NNN  22:28    1:55m  0.00s  0.08s sshd-session: robbitay [priv]
robbitay          -                22:28    1:55m  0.00s  0.13s /usr/lib/systemd/systemd --user
```
- [ ] List information about hard drives and partitions with `lsblk`
```
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
vda     253:0    0   25G  0 disk
├─vda1  253:1    0 23.9G  0 part /
├─vda13 253:13   0 1023M  0 part /boot
├─vda14 253:14   0    4M  0 part
└─vda15 253:15   0  106M  0 part /boot/efi
vdb     253:16   0  482K  1 disk
```
- [ ] List RAM information with `free`
```
               total        used        free      shared  buff/cache   available
Mem:          984004      344628      193224        4140      600100      639376
Swap:              0           0           0
```
- [ ] All session command-line history is written to `home/[username]/.bash_history`
- [ ] See all services status: `service --status-all`
```
 [ + ]  apparmor
 [ + ]  apport
 [ - ]  console-setup.sh
 [ + ]  cron
 [ - ]  cryptdisks
 [ - ]  cryptdisks-early
 [ + ]  dbus
 [ - ]  grub-common
 [ - ]  iscsid
 [ - ]  keyboard-setup.sh
 [ + ]  kmod
 [ - ]  open-iscsi
 [ - ]  open-vm-tools
 [ + ]  plymouth
 [ + ]  plymouth-log
 [ + ]  procps
 [ - ]  rsync
 [ - ]  screen-cleanup
 [ + ]  ssh
 [ + ]  sysstat
 [ + ]  ufw
 [ + ]  unattended-upgrades
 [ - ]  uuidd
```
- [ ] List all users with `cat /etc/passwd` (or `cut -d: -f1 /etc/passwd` which splits by `:` and takes index 1 piece from each line)
- [ ] List all groups with `cat /etc/group` (or `cut -d: -f1 /etc/group`)
- [ ] List groups for user with `groups [username]`. List users in a group with `getent group [group]` (or just look in `/etc/group`)
- [ ] See `/usr/share/app-install-data/desktop` for a list of programs that can be installed through the ubuntu software center
- [ ] *dbus* is a protocol to send messages (like HTTP) that is lower overhead and more versatile. We should look into how it works more
- [ ] `dosfstools` is a package that provides tools for checking MS-DOS FAT filesystems
- [ ] Zenity allows you to open native dialog boxes (like "Open File" and confirmation dialogs) on Linux [Gitlab](https://gitlab.gnome.org/GNOME/zenity)
	- [ ] GTK app? GNOME? (GTK 4.6 and libadwaita 1.2) "Not a core GNOME application, it's a GNOME Extra Apps"
	- [ ] `zenity --about` - Zenity 4.2.0 [Website](https://gitlab.gnome.org/GNOME/zenity)
	- [ ] `zenity --file-selection` - "Open File" dialog box
- [ ] To add environment variables we can edit `/etc/environment`?
- [ ] [How to diagnose audio problems on Linux](https://www.linux.org/threads/troubleshooting-audio-problems-in-linux.55508/) 
- [ ] Terminal-based text editors
	1. [Vim (and NeoVim) - TUI Text Editor](Vim%20(and%20NeoVim)%20-%20TUI%20Text%20Editor.md)
	2. [Nano - TUI Text Editor](Nano%20-%20TUI%20Text%20Editor.md) (aka pico)
	3. Echo
	4. Emacs
	5. Micro
- [ ] [List of Display Managers](https://wiki.archlinux.org/title/Display_manager) (login screen). Lubuntu installation has [SDDM](https://github.com/sddm/sddm) 
- [ ] "installed" applications usually put a `.desktop` file in `/usr/share/applications` in order to have an entry show up in the start menu [Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry/latest/file-naming.html) 
- [ ] `greetd`: Simpler TUI based login manager instead of SDDM (HMC person uses)
- [ ] Niri is a better wayland compositor that works with NVidia better for Hyperland
	- [ ] Hyperland maintainers kind of suck
- [ ] pixmaps are what define the image for a executable
	- [ ] `/usr/share/pixmaps`
	- [ ] `~/.local/share/icons`
- [ ] Unix research conducted at the University of California, Berkeley. Originally known as "BSD Unix" or "Berkeley Unix," it is now simply referred to as BSD, standing for Berkeley Software Distribution.
- [ ] Created [[Raspberry Pi Notes]] on August 2nd 2026
- [ ] 

---
# Commands
## Cheatsheet
- [ ] `du -a /home | sort -n -r | head -n 5`: List largest directories
- [ ] `ls -Shog`: List files sorted by size and minimal other information
- [ ] `uptime`: Show server load
- [ ] `ncdu` or `df -h` or `lsblk`: Find what folders are using disk space
- [ ] `sudo apt-get autoremove`: Remove AWS headers
- [ ] `sudo ls -Shog /var/lib/mysql`: Check database disk usage
- [ ] `apt list --installed`: List all installed packages
- [ ] `aptitude search '~i!~M'` or `apt-mark showmanual`: List all packages that were explicitly installed (not just auto-installed as a dependency) or look in `/var/log/apt/history.log`
- [ ] `apt-file search [file_path]`: Find which package a file comes from. For example `apt-file search /usr/include/GL/gl.h` reports `libgl-dev`
- [ ] `sudo update-alternatives --config [name]`: Change the default program. For potentnial program names see `/etc/alternatives`. For example `x-terminal-emulator` determines the default graphical terminal
- [ ] `[command] | more`: Paginate the stdout from a command to make it easier to read through
- [ ] `tree -if | grep .txt`: Recursively find all files in this folder (or subfolders) that have `.txt` in the name (use whatever grep pattern you want). Better than grepping `ls` because each line has full path to the file so matching the line tells you where it is at in the subfolders
- [ ] `neofetch`/`fastfetch`: Display an ASCII logo of the distro and some information about the system. Can also look at `/etc/os-release`
- [ ] `lspci -nnk`: Check which drivers are running the graphics card
- [ ] `id -u` and `id -g`: Prints the ID for the current user and group?
- [ ] `cat ~/.bash_history | grep "sudo apt install"`: List all the packages that have been installed (recently maybe? Not sure how long `.bash_history` persists)
- [ ] `dnf repoquery --providers-of=requires [package]`: List what packages are required by a particular package
- [ ] 
## Basic
- [ ] `clear` *Clear the terminal history*
- [ ] `info [gnu_command]`: ==TODO:==
- [ ] `man [command/function/etc]`: Show the manual for the given command/function/etc.
	- [ ] Multiple entries for the same name can exist as long as they exist in separate *Sections*. **Possible sections:**
		1. Executable Programs or shell commands
		2. System calls (functions provided by the kernel)
		3. Library calls (functions within program libraries)
		4. Special files (usually found in `/dev`)
		5. File formats and conventions, e.g. `/etc/passwd`
		6. Games
		7. Miscellaneous (including macro packages and conventions)
		8. System administration commands (usually only for root)
		9. Kernel routines (non-standard)
- [ ] `rm` *remove files/directories*
	- [ ] `rm -R [file/folder]` = Recursive (required to remove a directory)
	- [ ] `rm -f [file/folder]` = Force (ignore non-existant files and arguments)
	- [ ] `rm -i [file/folder]` = Prompt before all removals (also try `-I` for slightly less intrusive prompts)
- [ ] `rm` *remove files/directories*
	- [ ] `rm -R [file/folder]` Recursive (required to remove a directory)
	- [ ] `rm -f [file/folder]` Force (ignore nonexistant files and arguments)
	- [ ] `rm -i [file/folder]` Prompt before all removals (also try `-I` for slightly less intrusive prompts)
- [ ] `ls` *list the contents in a directory*
	- [ ] `ll` Long listing format with each file/directory on a single line and size and access information displayed
	- [ ] `lsd` A variant of ls that can be installed that is nicer and newer
	- [ ] `ls -a` Hidden files included
	- [ ] `ls -A` Do not list . and ..
	- [ ] `ls -h` Human readable file sizes
	- [ ] `ls -R` Recursively list subdirectories
	- [ ] `ls -S` Sort by file size
	- [ ] `ls -o` 
	- [ ] `ls --hyperlink`: Make each output a clickable [VTE hyperlink](https://gist.github.com/egmontkob/eb114294efbcd5adb1944c9f3cb5feda) 
- [ ] `mkdir` *make a new directory*
	- [ ] `mkdir -p [directory/directory/directory]` Make parent directories if needed
- [ ] `which` *Print where an executable lies* (also see `whereis` which is similar but different)
	- [ ] `which mkdir` prints `/usr/bin/mkdir`
- [ ] `chmod` *Change the attributes of a file*
	- [ ] `chmod +x /path/to/file` Makes the file executable
- [ ] `apt` *apt provides a high-level command-line interface for the package management system*
	- [ ] `apt list --installed` List all the installed packages
	- [ ] `apt search [regex]` Find all packages matching a regular expression
	- [ ] `apt autoremove` Removes packages that were installed to satisfy dependencies that are no longer needed
	- [ ] `apt show [package]` Show information about a specific package
	- [ ] `apt edit-sources` Edit the `sources.list` files in a text editor (found in `etc/apt/sources.list` and `etc/apt/sources.list.d/`)
	- [ ] `apt update` Updates the package system I guess. Often used before installing new packages
- [ ] `apt-get` *apt-get is a command line interface for retrieval of packages and information about them from authenticated sources and for installation, upgrade, and removal of packages together with their dependencies*
	- [ ] `apt-get install [package]`  Install a new package
	- [ ] `apt-get remove [package]`  Remove a previously installed package
	- [ ] `apt-get upgrade [package]` Upgrade/update a package to a newer version
	- [ ] `apt-get purge [package]` Similar to remove but configuration files are deleted as well
	- [ ] `apt-get download [package]` Downloads the binary package into the current directory
- [ ] `dpkg` *dpkg is a tool to install, build, remove and manage Debian packages. The primary and more user-friendly front-end for dpkg is aptitude*
	- [ ] `dpkg -i [filename]` Installed a .deb package file
	- [ ] `dpkg-query -L [package]` List the items installed by a package
- [ ] `ar` *creates, modifies, and extracts from archives*
	- [ ] `ar x [archive]` Extracts all the items in the archive to the current directory (use `-v` to list files as it extracts)
	- [ ] `ar d [archive] [member]` Deletes items in an archive
	- [ ] `ar q [archive] [member]` At items to an archive
	- [ ] `ar t [archive]` List the members of an archive
- [ ] `tar` *create, modify, or extract the contents of a tar archive*
	- [ ] `tar -x -f [archive]` Extracts the contents of an archive
	- [ ] `tar -t -f [archive]` List the contents of an archive
	- [ ] `tar -C [directory] -x -f [archive]` Changes the directory before extracting the contents of an archive
- [ ] `file` *a file contents type guesser*
	- [ ] `file [filename]` looks at the contents of `[filename]` and guesses what format the file is
	- [ ] `file [filename] --mime` prints the actual mime type instead of human readable format
- [ ] `find` *search for files*
- [ ] `xargs` *search stdin, find patterns, call some command for every pattern found?*
- [ ] `grep` *searches various inputs for matches to expressions*
	- [ ] `ls | grep [string]` prints out lines of ls that match `[string]`
	- [ ] `ls | grep -G [regex]` uses the regular expression to match and print lines from ls output
	- [ ] `grep so..thing` matches things like `something`, `sooothing`, and `sourthing`
- [ ] `readlink -f [file]`: Figure out where a symlink goes
- [ ] `env` *Print out the current environment variables*
	- [ ] You can also edit `/etc/environment` to change the default environment variables for all programs (requires restart after editing?)
	- [ ] ==*WARNING*== You cannot do `PATH="/my/bin:$PATH"` because `$PATH` does not expand properly. This caused me a while of debugging on Raspberry Pi. Eventually I changed it to a literal with all the regular paths added: `PATH=/home/robbitay/my/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games`
- [ ] `source [file]`: Run a particular file as a bash script
- [ ] `ln` *Make links between files/folders*
	- [ ] `ln /etc/share/applications ./ApplicationsFolder`
- [ ] 
## Random Useful
- [ ] `time` *used to display time and other information about a program*
	- [ ] `time ./[executable]` Runs an executable and when finished will display the timing information about that executable (==TODO:== Figure out how to get the `--format` option on time to work)
- [ ] `wc` *write newline, word, and byte counts for files*
	- [ ] `wc [filename]` Writes the newline count, the word count, and the byte count for a file
- [ ] `sol` *play solitaire*
- [ ] `apg` *generates password based off various input parameters*
- [ ] `bc` *a interpreter/compiler for the IEEE scientific bc language*
- [ ] `look` *from bsdmainutils, look for lines in a file that start with a prefix*
	- [ ] `look [prefix]` Search `/usr/shar/dict/words` for all words with given prefix
	- [ ] `look [prefix] [file]` Search a file for all lines beginning with given prefix
- [ ] `cal` *displays a simple calendar*
	- [ ] `ncal` alternate formatted calendar
- [ ] `printerbanner` *prints a single line from the standard input as a large, high quality, banner*
	- [ ] `printerbanner -w 60` prints the input line with a width of 60 characters (instead of default 132)
- [ ] `logger` *make entries into the system log*
- [ ] `bzip2` *compresses file using bzip2 compression*
	- [ ] `bzip2 [filename]` Compresses the file into one of the same name with `.bz2` at the end
	- [ ] `bzip2 -d [filename]` Decompresses a previously compressed file
- [ ] `curl` *make web reqests over HTTPS, FTP, and other protocols*
	- [ ] `curl [url]` requests the contents of the url and displays the result
	- [ ] `curl [url] --data-urlencode [name]=[value]` Requests a url with a url-encoded content body
- [ ] `dc` *a stack based calculator?*
- [ ] `diff` *compares two files and produces a list of changes*
	- [ ] `diff [left] [right]` Compare the contents of 2 files (line-by-line)
	- [ ] `diff3 [left] [middle] [right]` Compare the contents of 3 files
	- [ ] `sdiff [left] [right] -o [filename]` Runs an interactive merging two and outputs the result to `[filename]`
	- [ ] `diff [left] [right] | diffstat` Produces an output like: `[file] |  3 ++- \n  1 file changed, 2 insertions(+), 1 deletion(-)`
	- [ ] `cmp [left] [right]` compares the contents of both files byte by byte
- [ ] `dig` *used to look up entries on DNS servers*
	- [ ] `dig [server] [name] [type]`
- [ ] `eject` *ejects a cdrom or mounted storage device*
	- [ ] `eject` Open the cdrom drive (`-t` to close the cdrom drive)
- [ ] `evince` *a PDF/Document viewer*
- [ ] `fakeroot` *simulates root privelages*
- [ ] `ffmpeg` *a command line tool to convert multimedia files between formats*
- [ ] `ffserver` *a multimedia streaming server for live broadcasts*
- [ ] `ffplay` *a simple media player based on SDL and the FFmpeg libraries*
- [ ] `ffprobe` *a simple multimedia stream analyzer*
- [ ] `qt-faststart` *a utility to rearrange Quicktime files*
- [ ] `ffmpegthumbnailer` *a utility for making thumbnails for multimedia files*
- [ ] `geary` *an email client GUI application*
- [ ] `gedit` *a graphical text editor*
- [ ] `gs` *(ghostscript) a PDF viewer?*
- [ ] `loginctl` *Display information about current desktop sessions*
	- [ ] `loginctl show-session [session-id]` Show extended information about a particular session (run `loginctl` without args to get session IDs)
- [ ] `sddm` The Simple Desktop Display Manager (used for Lubuntu login screen aka "greeter")
	- [ ] https://github.com/sddm/sddm
- [ ] `xrandr` *set resolution, orientation and/or reflection of monitors*
	- [ ] [How Can I change SDDM Screen Resolution](https://forums.freebsd.org/threads/how-can-i-change-sddm-screen-resolution.88704/)
- [ ] `alsamixer`: An ncurses based TUI that allows you to change audio devices and volume
- [ ] `readelf`: ==TODO:==
- [ ] `file [any_file_type]`: Tried to determine the type of file and prints out information about that specific file
- [ ] `lsof`: List open files for a running program
	- [ ] `lsof -p [PID]`: List open file handles for program with specific PID
- [ ] `fdisk` *Manipulate disk partition table*
	- [ ] `sudo fdisk -l`: List a bunch of information about disks, partitions, and file systems
- [ ] 
## Other
- [ ] 

---
# Packages
- [ ] `apt-file`: Allows you to search through apt packages for a particular file name (useful for finding which package a binary might have come from). Make sure to run `sudo apt-file update` after installing
- [ ] `libx11-dev`: Includes X11 libraries and header files for compiling applications that open X11 windows (also see `libxcursor-dev`, `libxi-dev`, `libxinerama-dev`, and `libxrandr-dev`)
- [ ] `libwayland-dev`: Includes Wayland libraries and header files for compiling Wayland applications
- [ ] `libfontconfig-dev`: Includes Fontconfig libraries and header files. Fontconfig is a generic font configuration library. It's designed to locate fonts within the system and select them according to requirements specified by applications
- [ ] `libgtk-3-dev` and `libgtk-4-dev`: Includes GTK libraries and header files for compiling GTK UI applications (also `gtk-4-examples` and run `gtk4-demo` and see [Github](https://github.com/GNOME/gtk/blob/main/demos/gtk-demo/)).
	- [ ] Then do `pkg-config --cflags gtk4` to get C compiler flags for linking with GTK
- [ ] `libdbus-1-dev`: Includes D-Bus libraries and header files for compiling programs that do inter-process communication (IPC)
- [ ] `libgl-dev`: 
- [ ] `ubuntu-restricted-extras`: Things that have to be opt-in because of legal issues in some countries (like video/audio codecs, fonts, etc.)
- [ ] `ffmpeg` and `libavcodec61` and `libavcodec-extra`
- [ ] `net-tools` for `ifconfig` and others (`arp`, `netstat`, `rarp`, `nameif` and `route`)
- [ ] `cmake`: CMake cross-compilation utility
- [ ] `build-essential`: Required tools for building Debian packages
	- [ ] Depends on `libc6-dev`|`libc-dev`, `gcc`, `g++`, `make`, `dpkg-dev`
- [ ] `numlockx`: Enable numlock by default after rebooting
- [ ] `python3`, `python-is-python3`, `python3-pip`, `python3-full`
- [ ] `bear`: A tool for generating `compile_commands.json` for use with *clangd* (a language server for C, see LSP plugin for Sublime)
- [ ] `keepassxc`: KeePass client GUI (way better than `keepass2`)
- [ ] `delta`

---
# Linux Mint Information
- [ ] Linux Mint 22 x86_64
	- *Linux Mint is an Ubuntu-based distribution whose goal is to provide a classic desktop experience with many convenient, custom tools and optional out-of-the-box multimedia support. It also adds a custom desktop and menus, several unique configuration tools, and a web-based package installation interface. Linux Mint is compatible with Ubuntu software repositories. Besides its Ubuntu-based flavour, the project also produces a separate "Debian" edition (called LMDE), based on the latest stable Debian version.*
- [ ] Kernel 6.8.0-50-generic
- [ ] Shell: bash 5.2.21
- [ ] Desktop Environment: Cinnamon 6.2.9
- [ ] Window Manager: Muffin (fork of Mutter)
- [ ] Terminal: gnome-terminal
- [ ] CPU: Intel i7-6700K
- [ ] GPU: NVIDIA GeForce RTX 3060 Ti GDDR6X
- [ ] `/dev/sda5`=Linux Hard Drive     `/dev/sdb2` = Local Disk (C:)     `/dev/sda4` = Local Disk (D:)    `/dev/sdc2` = BigSSD (F:)    `/dev/sde1` = Block (?:)
### Cinnamon
- [ ] Cinnamon, forked from GNOME Shell, is the "shell" of Cinnamon. It provides the user interface such as panels, hot corners, menus etc. The ui is written in JavaScript, while its core libraries are written in C
- [ ] https://projects.linuxmint.com/cinnamon/
- [ ] https://github.com/linuxmint/Cinnamon
- [ ] https://github.com/linuxmint/cinnamon-control-center
- [ ] https://github.com/linuxmint/cinnamon-desktop
- [ ] https://github.com/linuxmint/mdm
- [ ] https://github.com/linuxmint/cinnamon-menus
- [ ] https://github.com/linuxmint/muffin
- [ ] https://github.com/linuxmint/nemo
- [ ] https://github.com/linuxmint/nemo-extensions
- [ ] https://github.com/linuxmint/cinnamon-screensaver
- [ ] https://github.com/linuxmint/cinnamon-session
- [ ] https://github.com/linuxmint/cinnamon-settings-daemon
- [ ] https://github.com/linuxmint/cinnamon-spices-applets
- [ ] https://github.com/linuxmint/cinnamon-spices-desklets
- [ ] https://github.com/linuxmint/cinnamon-spices-extensions
- [ ] https://github.com/linuxmint/cinnamon-spices-themes
- [ ] https://github.com/linuxmint/cinnamon-translations

---
# FontConfig [Link](https://www.freedesktop.org/wiki/Software/fontconfig/)
- [ ] [How to use the Fontconfig Library with C](https://www.camconn.cc/post/how-to-fontconfig-lib-c/)
- [ ] [Stack Overflow: Locating fonts on Linux (in C++)](https://stackoverflow.com/questions/4347277/locating-fonts-on-linux-in-c)
- [ ] [font-manager (package for viewing .ttf files)](https://github.com/FontManager/font-manager)
- [ ] On WSL we have to install `libfontconfig1-dev` package to get the `fontconfig/fontconfig.h` header
- [ ] 


---
# Distro Notes
#### General Notes
- [ ] [Which linux distribution should I start with - Reddit](https://www.reddit.com/r/linuxquestions/comments/16qpflu/which_linux_distribution_should_you_start_with/)
	- [x] **Ubuntu** - Popular, great for general use [Flavors](https://ubuntu.com/desktop/flavors)
		- [ ] **Edubuntu** - For educational world (teachers and students, lots of educational software available)
		- [x] **Kubuntu** - *KDE Plasma* desktop environment
		- [x] **Lubuntu** - Lighweight and simple. *LXQt* desktop environment
		- [ ] **Ubuntu Budgie** - The official flavor of Ubuntu
		- [x] **Ubuntu Cinnamon** - Cinnamon Desktop, *GNOME 2* desktop environment
		- [ ] **Ubuntu Kylin** - For chinese users, Ubuntu Kyline User Interface *(UKUI)*
		- [ ] **Ubuntu MATE** - Configurable and best for older hardware
		- [ ] **Ubuntu Studio** - Pre-configured for content creation
		- [ ] **Ubuntu Unity** - Combines *Unity* with Ubuntu
		- [ ] **Xubuntu** - Comes with *Xfce* desktop environment
	- [x] **Linux Mint** - Based on Ubuntu, more Windows-like, beginner friendly
	- [ ] **Debian** - Stable and robust
	- [x] **Fedora** - Cutting-edge (Dylan did Fedora 5-6 Redhat, did Void Linux for a while and then came back)
	- [ ] **OpenSUSE** [Website](https://get.opensuse.org/) - (Two versions: Leap, and Tumbleweed. Regular release, and rolling release, respectively)
	- [ ] **Arch Linux** - Rolling-release, minimal and highly customizable
	- [ ] **FreeBSD** - Not Linux, different Kernel (OS came from fork of BSD) (Dylan says it's *super cool*, and extremely stable, zfs file system, kind of btrfs)
	- [ ] **GhostBSD** [Website](https://www.ghostbsd.org/) - FreeBSD-based OS with MATE Desktop Environment, GTK UI,
	- [ ] **Gentoo** [Website](https://www.gentoo.org/) - Source-based, compile everything
	- [ ] **Kali Linux** - For ethical hacking
	- [ ] **Raspbian** - Raspberry Pi
	- [ ] **CentOS** - Excellent for server environments
	- [ ] **Tails** - Privacy-focused, leaves no trace, routes through Tor
	- [ ] **Adelie** [Link](https://www.adelielinux.org/) - Focused on performance (KDE is the creators preferred desktop platform) runs on like 600MB of RAM
	- [ ] **Mandreep**? - No longer exists?
	- [ ] Manjaro - Is also bad like pacman
	- [ ] Pacman is bad, it'll break your operating system sometimes if you don't use it for too long
	- [ ] **Pop! OS** [Website](https://system76.com/pop/)
- [ ] The most recent Linux kernel (and earlier versions) can always be found in the [Linux Kernel Archives](https://www.kernel.org/)
- [ ] What desktop environments are available for which linux distros?
	- [ ] [What is the core difference between the Linux distros? - Reddit](https://www.reddit.com/r/linux4noobs/comments/vm2r2s/what_is_the_core_difference_between_the_linux/)
	- [ ] **Linux Mint** is essentially **Ubuntu LTS** with snap disabled and some custom repositories, but there's nothing stopping you from installing **Ubuntu LTS**, disabling snap and adding **Linux Mint**'s repositories.
	- [ ] **Void Linux**, **Devuan**, **Artix** and **Antix** don't use *systemD*, favouring other init systems (like *runit*)
	- [ ] **Alpine** doesn't use any *gnu* software
	- [ ] **Nix OS** uses a configuration file to set it up, allowing you to install it company wide and using this one file making every system the same as the next
	- [ ] **QUBES** and **Alpine** main usage is *containerization*
	- [ ] **Puppy** and **Damn Small Linux** aim to be as lightweight as possible and old machine friendly
	- [ ] **Slackware** doesn't have a package manager
- [ ] Which package managers are available?
	- [ ] **apt** - "good but can be a bit fickle with meta groups and trying to uninstall things I wanted"
	- [ ] **dnf** - "was slow"
	- [ ] **pacman** - "was perfect"
- [ ] What standard library is the system built on?
	- [ ] **GNU libc**
	- [ ] **uClibc**
- [ ] https://3d.bk.tudelft.nl/gagugiaro/tutorials/pdf/VirtualBox_Kubuntu_Installation_Guide.pdf
- [ ] [How do I tell if X11 or Wayland is being used?](https://unix.stackexchange.com/questions/202891/how-to-know-whether-wayland-or-x11-is-being-used)
	- [ ] run `loginctl` and get session ID
	- [ ] `loginctl show-session 1 -p Type`
- [ ] [List of GTK applications](https://en.wikipedia.org/wiki/List_of_GTK_applications)
	- [ ] GTK-based desktops: *GNOME*, *Cinnamon*, *LXDE*, *MATE*, *Pantheon*, *Sugar*, *Xfce*, and *ROX Desktop*
- [ ] 
---
#### Ubuntu Desktop
- [ ] **Display Server** = X.Org Server and Wayland
- [ ] **Sound** = PipeWire
- [ ] **Multimedia** = Totem and Rythmbox
- [ ] **Window Manager** = Mutter
- [ ] **Desktop** = GNOME Desktop Environment [About GNOME on Ubuntu](Images/AboutGnomeOnUbuntu.png)
- [ ] **Primary Toolkit** = GTK
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = Thunderbird
- [ ] **Package Manager** = `apt`
- [ ] **Terminal** = GNOME Terminal
- [ ] **Task Manager** = ?
- [ ] **Text Editor** = GNOME Text Editor and Nano
---
#### Kubuntu ([Screenshot](Images/Kubuntu_desktop_screenshot.png)) ([KDE Plasma Welcome](Images/kde_plasma_welcome_screenshot.png))
- [ ] **Display Server** = X.Org Server and Wayland (Wayland Desktop Session)
- [ ] **Sound** = PipeWire
- [ ] **Multimedia** = VLC and Elisa [Screenshot](Images/elisa_screenshot.png) 
- [ ] **Window Manager** = KWin
- [ ] **Desktop** = Plasma Desktop
- [ ] **Primary Toolkit** = Qt
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = Thunderbird
- [ ] **Package Manager** = `apt`
- [ ] **Terminal** = Konsole [Screenshot](Images/Konsole_screenshot.png) 
- [ ] **Task Manager** = ?
- [ ] **Text Editor** = ?
---
#### Lubuntu ([Screenshot](Images/Lubuntu_desktop_screenshot.png)) ([Manual](https://manual.lubuntu.me/stable/))
- [ ] **Display Server** = X.Org Server and Wayland (X11 Desktop Session)
- [ ] **Sound** = ?
- [ ] **Multimedia** = VLC
- [ ] **Window Manager** = Openbox
- [ ] **Desktop** = LXQt
- [ ] **Primary Toolkit** = Qt
- [ ] **Browser** = ?
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = ?
- [ ] **Package Manager** = `apt`/`apt-get`/`apt-cache`
- [ ] **Terminal** = QTerminal [Screenshot](Images/QTerminal_Screenshot.png) 
- [ ] **Task Manager** = ?
- [ ] **Text Editor** = ?
---
#### Ubuntu Cinnamon ([Screenshot](Images/UbuntuCinnamon_screenshot.png))
- [ ] **Display Server** = ?
- [ ] **Sound** = ?
- [ ] **Multimedia** = Rythmbox and "Videos"
- [ ] **Window Manager** = ?
- [ ] **Desktop** = Cinnamon (GNOME 2)
- [ ] **Primary Toolkit** = GTK?
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = ?
- [ ] **Package Manager** = `apt`
- [ ] **Terminal** = "Terminal" [Screenshot](Images/UbuntuCinnamonTerminal_screenshot.png) 
- [ ] **Task Manager** - System Monitor [Screenshot](Images/UbuntuCinnamonSystemMonitor_screenshot.png) 
- [ ] **Text Editor** = ?
---
#### Linux Mint ([Screenshot](Images/LinuxMint_screenshot.png))
- [ ] **Display Server** = X11
- [ ] **Sound** = ?
- [ ] **Multimedia** = Rythmbox, Celluloid, Hypnotix
- [ ] **Window Manager** = ?
- [ ] **Desktop** = Cinnamon
- [ ] **Primary Toolkit** = ?
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = ?
- [ ] **Package Manager** = `apt`
- [ ] **Terminal** = "Terminal" [Screenshot](Images/LinuxMintTerminal_screenshot.png) 
- [ ] **Task Manager** = ?
- [ ] **Text Editor** = ?
---
#### Fedora Workstation ([Screenshot](Images/FedoraWorkstation_screenshot.png))
- [ ] **Display Server** = X11 and Wayland (Wayland Desktop Session)
- [ ] **Sound** = PulseAudio [Wiki Link](https://fedoraproject.org/wiki/Audio)
- [ ] **Multimedia** = "Video Player", "Audio Player", "Image Viewer", "Document Viewer"
- [ ] **Window Manager** = ?
- [ ] **Desktop** = GNOME?
- [ ] **Primary Toolkit** = GTK?
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice
- [ ] **Email and PIM** = ?
- [ ] **Package Manager** = `dnf`
- [ ] **Terminal** = "Terminal" [Ptyxis](https://gitlab.gnome.org/chergert/ptyxis) [Screenshot](Images/FedoraWorkstationTerminal_screenshot.png) 
- [ ] **Task Manager** = System Monitor [Screenshot](Images/FedoraWorkstation_SystemMonitor_screenshot.png) 
- [ ] **Text Editor** = ?
---
#### Fedora KDE Plasma ([Screenshot](Images/FedoraKdePlasma_screenshot.png))
- [ ] **Display Server** = X11 and Wayland (Wayland Desktop Session)
- [ ] **Sound** = ?
- [ ] **Multimedia** = Dragon Player and Elisa
- [ ] **Window Manager** = ?
- [ ] **Desktop** = Plasma Desktop (KDE)
- [ ] **Primary Toolkit** = Qt
- [ ] **Browser** = Firefox
- [ ] **Office Suite** = LibreOffice and Okular
- [ ] **Email and PIM** = ?
- [ ] **Package Manager** = `dnf` (used to be `rpm` and `yum`) has parrallel downloads
- [ ] **Terminal** = Konsole [Screenshot](Images/FedoraKdeoPlasma_Konsole_screenshot.png) 
- [ ] **Task Manager** = System Monitor [Screenshot](Images/FedoraKdeSystemMonitor_screenshot.png) 
- [ ] **Text Editor** = KWrite

## Desktop VMs
---
### Ubuntu1
- [ ] **Ubuntu** 24.04.2 Desktop AMD64 - Downloaded June 24th 2025
- [ ] ISO File Name: `ubuntu-24.04.2-desktop-amd64.iso`
- [ ] Device Name: `Ubuntu1`
- [ ] Kernel Version: 6.14.0-37-generic
- [ ] [System Details](Images/UbuntuSystemInformation_screenshot.png)
- [ ] Shortcuts:
	- [ ] **Ctrl+Alt+T**: Launch Terminal
	- [ ] **Win+Alt+S**: Search (modified)
	- [ ] **Win+A**: Show All Apps (similar to Search hotkey but enabled by default)
	- [ ] **Ctrl+Alt+D**: Show Desktop
	- [ ] **Win+Shift+PageUp/PageDown**: Move window to next/previous workspace
	- [ ] **Alt+F2**: Show the run command prompt
- [ ] Settings Changes:
	- [ ] Multitasking -> Enable Active Screen Edges
	- [ ] Multitasking -> Set Fixed Number of Workspaces to 4
	- [ ] Multitasking -> Include apps from the current workspace only
	- [ ] Power -> Screen Blank = Never
	- [ ] Appearance -> Dark, Prussian Green
	- [ ] Ubuntu Desktop -> Desktop Icons -> Size = Small
	- [ ] Ubuntu Desktop -> Dock -> Auto-hide the Dock = Enabled
	- [ ] Ubuntu Desktop -> Dock -> Icon Size = 30
	- [ ] Ubuntu Desktop -> Dock -> Position on Screen = Bottom
	- [ ] Keyboard -> Keyboard Shortcuts -> Launchers -> Search = **Win+Alt+S** (replaces screen reader toggle hotkey)
	- [ ] Keyboard -> Keyboard Shortcuts -> Navigation -> Switch to workspace 1/2/3/4 = **Ctrl+Alt+1/2/3/4**
	- [ ] Keyboard -> Keyboard Shortcuts -> Screenshots -> Take a screenshot = **Print**
	- [ ] Keyboard -> Keyboard Shortcuts -> Screenshots -> Take a screenshot interactively = **Ctrl+Print**
	- [ ] Keyboard -> Keyboard Shortcuts -> Custom -> Launch System Monitor `gnome-system-monitor` = **Ctrl+Shift+Escape**
	- [ ] System -> Users -> Automatic Login = Enabled
	- [ ] System -> Date & Time -> Time Zone = PST (Los Angeles, United States) UTC-0800
	- [ ] System -> Date & Time -> Time Format = AM/PM
- [ ] In `/etc/apt/sources.list.d/ubuntu.sources` it defines two `deb` sources: `http://us.archive.ubuntu.com/ubuntu/` for *noble*, *noble-updates*, and *noble-backports* and `http://security.ubuntu.com/ubuntu` for *noble-security*
- [ ] `apt install libgtk-4-dev` which installed a bunch of dependencies
- [ ] 
### UbuntuClean
- [ ] **Ubuntu** 24.04.2 Desktop AMD64 - Downloaded June 24th 2025
- [ ] ISO File Name: `ubuntu-24.04.2-desktop-amd64.iso`
- [ ] 
### Kubuntu
- [ ] **Kubuntu** 25.10 Plasma 6.4 Qt 6 64-bit - Downloaded January 4th 2026
- [ ] ISO File Name: `kubuntu-25.10-desktop-amd64.iso`
- [ ] Selected "Normal Installation - Web browsers, utilities, office software, games, and media players"
- [ ] Doesn't event have `pkg-config` installed (can install with `sudo apt install pkgconf`)
- [ ] Installed `zenity` to test if CSwitch starts working. Zenity is **not** installed by default
- [ ] 
### Lubuntu
- [ ] **Lubuntu** 25.10 (Questing Quokka) LXQt 2.2.0 Desktop 64-bit - Downloaded January 4th 2026 [Download](https://lubuntu.me/downloads/)
- [ ] ISO File Name: `lubuntu-25.10-desktop-amd64.iso`
- [ ] Selected "Normal Installation - Web browsers, utilities, office software, games, and media players"
- [ ] Installed `zenity` to test if CSwitch starts working. Zenity is **not** installed by default
- [ ] 
### Ubuntu Cinnamon
- [ ] **Ubuntu Cinnamon** 25.10 (Questing Quokka) 64-bit PC (AMD64) desktop - Downloaded January 4th 2026 [Download](https://cdimage.ubuntu.com/ubuntucinnamon/releases/questing/release/)
- [ ] ISO File Name: `ubuntucinnamon-25.10-desktop-amd64.iso`
- [ ] 
### LinuxMintClean
- [ ] **Linux Mint** 22.2 Cinnamon "Zara" - Downloaded Dec 31st 2025
- [ ] ISO File Name: `linuxmint-22.2-cinnamon-64bit.iso`
- [ ] [Download](https://linuxmint.com/edition.php?id=322) [LinuxFreedom Mirror](https://linuxfreedom.com/linuxmint/linuxmint.com/stable/22.2/linuxmint-22.2-cinnamon-64bit.iso)
- [ ] Zenity is installed by default
- [ ] 
### FedoraWorkstation
- [ ] **Fedora** Linux 43 (Workstation Edition) Intel/AMD x86_64 (GNOME Desktop) - Downloaded Dec 31st 2025 [Download](https://www.fedoraproject.org/workstation/download)
- [ ] ISO File Name: `Fedora-Workstation-Live-43-1.6.x86_64.iso`
- [ ] Can't drag and drop files onto CSwitch
	- [ ] Seems like it's not my issue: [XWayland Crash during Drag-n-drop Firefox](https://bugzilla.redhat.com/show_bug.cgi?id=2406998) [Fedora 43 GNOME Session Logout](https://bugzilla.redhat.com/show_bug.cgi?id=2408770)
- [ ] Zenity is installed by default
- [ ] 
### FedoraKdePlasma
- [ ] **Fedora** KDE Plasma Desktop 43 Intel/AMD x86_64 (KDE Plasma Desktop) - Downloaded Dec 31st 2025 [Download](https://www.fedoraproject.org/kde/download)
- [ ] ISO File Name: `Fedora-KDE-Desktop-Live-43-1.6.x86_64.iso`
- [ ] `pkg-config gtk+-2.0 --cflags` returns nothing
- [ ] 
## Laptop VMs
---
### Ubuntu1
- [ ] **Ubuntu** 24.04.2 Desktop AMD64
- [ ] ISO File Name: `ubuntu-24.04.2-desktop-amd64.iso`
- [ ] Same settings changes as Ubuntu1 on Desktop
- [ ] Installed Sublime Text, Sublime Merge, KeePass2, and `libgtk-4-dev`
- [ ] 
### LinuxMint
- [ ] **Linux Mint** 22.2 Cinnamon "Zara" - Installed January 1st 2026
- [ ] ISO File Name: `linuxmint-22.2-cinnamon-64bit.iso`
- [ ] Can't drag and drop files onto CSwitch
- [ ] 
### FedoraWorkstation
- [ ] **Fedora** Linux 43 (Workstation Edition) Intel/AMD x86_64 (GNOME Desktop) - Installed January 1st 2026
- [ ] ISO File Name: `Fedora-Workstation-Live-43-1.6.x86_64.iso`
- [ ] 
### FedoraKdePlasma
- [ ] **Fedora** Linux 43 (Workstation Edition) Intel/AMD x86_64 (GNOME Desktop) - Installed January 1st 2026
- [ ] ISO File Name: `Fedora-Workstation-Live-43-1.6.x86_64.iso`
- [ ] 
### Kubuntu
- [ ] **Kubuntu** 25.10 Plasma 6.4 Qt 6 64-bit - Installed January 4th 2026
- [ ] ISO File Name: `kubuntu-25.10-desktop-amd64.iso`
- [ ] Selected "Normal Installation - Web browsers, utilities, office software, games, and media players"
- [ ] Can't install Guest Additions
- [ ] 
### Lubuntu
- [ ] **Lubuntu** 25.10 (Questing Quokka) LXQt 2.2.0 Desktop 64-bit - Installed January 4th 2026
- [ ] ISO File Name: `lubuntu-25.10-desktop-amd64.iso`
- [ ] Selected "Normal Installation - Web browsers, utilities, office software, games, and media players"
- [ ] 
### Ubuntu Cinnamon
- [ ] **Ubuntu Cinnamon** 25.10 (Questing Quokka) 64-bit PC (AMD64) desktop - Installed January 4th 2026
- [ ] ISO File Name: `ubuntucinnamon-25.10-desktop-amd64.iso`
- [ ] Hit some "internal errors" while running in the Live version
- [ ] End of install declared there was errors and I should retry installation
- [ ] s


# List of Programs to Install on Linux
---
- [ ] Sublime Text 
- [ ] Sublime Merge
- [ ] KeePass2
- [ ] Spotify
- [ ] Discord
- [ ] Revolt
- [ ] Obsidian
- [ ] BeyondCompare
- [ ] Git
- [ ] Tilix
- [ ] Micro
- [ ] Nano
- [ ] Fred
- [ ] CSwitch