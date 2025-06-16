## Notes
- [ ] Desktop Compiler Version: **v15.0.0**
- [ ] Install Location: `C:/MinGW/bin/gcc.exe`
- [ ] Avoid GCC on Windows because it doesn't have pdb support
## CLI Options
- [ ] `-D [DEFINE_NAME]{=VALUE}`: Sets a preprocessor define (optionally to a value)
- [ ] `-I [PATH]`: Adds a directory for searching when resolving `#include`s
- [ ] `-g3`: Produce debugging information in the operating system's native format (3 = ?)
- [ ] `-MD`: (MSVC Option) Use the multithread-specific and DLL-specific version of the run-time library
- [ ] `-MF [FILE_NAME]`: When used with the driver options -MD or -MMD, -MF overrides the default dependency output file
- [ ] `-std=[VERSION]`: Specify which version of C/C++ language we should compile for
#### Embedded/Playdate Related Options
- [ ] `-mthumb`: Requests that the compiler targets the T32 (Thumb) instruction set instead of A32 (Arm)
- [ ] `-mcpu=cortex-m7`: Enables code generation for a specific Arm processor
- [ ] `-mfloat-abi=hard`: Use hardware instructions for floating-point operations
- [ ] `-mfpu=fpv5-sp-d16`: Specifies the target FPU architecture, that is the floating-point hardware available on the target. (Armv7 FPv5-SP-D16 floating-point extension)
- [ ] `-specs=nano.specs`: Required for things like `_read`, `_write`, `_exit`, etc. to not be pulled in as requirements from standard library [Undefined Reference to sbrk](https://stackoverflow.com/questions/5764414/undefined-reference-to-sbrk) and [C API Converting String to Float](https://devforum.play.date/t/c-api-converting-string-to-float/10097)
- [ ] `-specs=nosys.specs`: ?
- [ ] `-gdwarf-2`: Produce debugging information in DWARF version 2 format (if that is supported). This is the format used by DBX on IRIX 6. With this option, GCC uses features of DWARF version 3 when they are useful; version 3 is upward compatible with version 2, but may still cause problems for older debuggers.
- [ ] 