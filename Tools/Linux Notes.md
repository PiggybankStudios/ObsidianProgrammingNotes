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
- [ ] 