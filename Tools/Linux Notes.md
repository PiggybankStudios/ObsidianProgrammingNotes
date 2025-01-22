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
- [ ] 