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
- [ ] Fonts are stored in `/usr/share/fonts` You can find a font using `fc-match [font_name]` (optionally pass `--format=%{file}`)
- [ ] 
## Linux Mint Information
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
## Notes From Dylan Conversations
- [ ] Ubuntu company is called "Canonical"
- [ ] IBM bought redhat
- [ ] Fedora runs perfectly on PowerPC stuff because IBM sorta owns PowerPC
- [ ] Snap packs (Ubuntu), flatpak (Fedora), has all the dependencies bundled with it
- [ ] [Void Linux](https://voidlinux.org/)
- [ ] [Chimera Linux](https://chimera-linux.org/)
- [ ] [DNF Package Manager](https://docs.fedoraproject.org/en-US/quick-docs/dnf/) (for Fedora)
- [ ] [Running GUI Applications on WSL](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)
- [ ] gparted or kparted partition-manager?
## FontConfig [Link](https://www.freedesktop.org/wiki/Software/fontconfig/)
- [ ] [How to use the Fontconfig Library with C](https://www.camconn.cc/post/how-to-fontconfig-lib-c/)
- [ ] [Stack Overflow: Locating fonts on Linux (in C++)](https://stackoverflow.com/questions/4347277/locating-fonts-on-linux-in-c)
- [ ] [font-manager (package for viewing .ttf files)](https://github.com/FontManager/font-manager)
- [ ] On WSL we have to install `libfontconfig1-dev` package to get the `fontconfig/fontconfig.h` header
- [ ] 