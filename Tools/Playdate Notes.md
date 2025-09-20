## Notes
- [ ] Playdate SDK Versions:
	- Previously used 2.0.3 and 2.1.0
	- Desktop was on 2.1.1
	- Updated to 2.7.4 on June 14th 2025
- [ ] Install Path: `F:\Programs\PlayDateSDK`
	- `bin\PlaydateSimulator.exe`
	- `bin\pdc.exe`
	- `bin\pdutil.exe`
- [ ] Compiler [Download ](https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads)
	- Path: `F:\Programs\arm-gnu-toolchain-12.3\bin\arm-none-eabi-gcc.exe`
	- `arm`: ARM (typically 32-bit ARM Cortex-M/R/A)
	- `none`: No OS
	- `eabi`: Embedded Application Binary Interface
- [ ] 
## `pdc.exe` CLI Options
```
usage: pdc [-sdkpath <path>] [-I <path>] [-s] [-u] [-m] [--version] <input> [output]
  input: folder containing scripts and assets (or lua source, with -m flag)
  output: folder for compiled game resources (will be created, defaults to <input>.pdx)
  -sdkpath: use the SDK at the given path instead of the default
  -I/--libpath: add the given path to the list of folders to search when resolving imports
  -s/--strip: strip debug symbols
  -u/--no-compress: don't compress output files
  -m/--main: compile lua script at <input> as if it were main.lua
  -v/--verbose: verbose mode, gives info about what is happening
  -q/--quiet: quiet mode, suppresses non-error output
  -k/--skip-unknown: skip unrecognized files instead of copying them to the pdx folder
  --version: show pdxversion
```
- [ ] 