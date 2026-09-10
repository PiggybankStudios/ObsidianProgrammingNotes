- [ ] [Website](https://ninja-build.org/) [Github](https://github.com/ninja-build/ninja) [v1.13.2](https://github.com/ninja-build/ninja/releases/tag/v1.13.2) [Manual](https://ninja-build.org/manual.html) 
- [ ] Installed **Ninja v1.13.2** on MacBook Pro on July 27th 2026 (placed in `.local/bin/`)
- [ ] By default it looks for a `build.ninja` file in the current directory
- [ ] CMake: A widely used meta-build system that can generate Ninja files on Linux as of CMake version 2.8.8. Newer versions of CMake support generating Ninja files on Windows and Mac OS X too.
- [ ] You can set `NINJA_STATUS` in order for make ninja print out things before a rule being run (See [Manual - Environment Variables](https://ninja-build.org/manual.html#_environment_variables))
- [ ] Example ninja file:
```ninja
# Set a 'variable' called "cflags"
cflags = -Wall

# Declare a rule named "cc"
rule cc
  command = gcc $cflags -c $in -o $out

build foo.o: cc foo.c
```
- [ ] Manual: `misc/ninja_syntax.py` in the Ninja distribution is a tiny Python module to facilitate generating Ninja files. It allows you to make Python calls like `ninja.rule(name='foo', command='bar', depfile='$out.d')` and it will generate the appropriate syntax. Feel free to just inline it into your project’s build system if it’s useful.
- [ ] 