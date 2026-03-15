- [ ] Installed Sublime Text Packages: `LSP`, `LSP-clangd`
- [ ] Since `clangd` was not installed on the system, LSP-clangd package seems to have downloaded it from Github into `~/.cach/sublime-text/Package Storage/LSP-clangd/clangd_21.1.8/`
- [ ] We can use [Bear](https://github.com/rizsotto/Bear) or [compiledb](https://github.com/nickdiego/compiledb) to generate a `compile_commands.json` file and place it into the root of the project
- [ ] [Reddit - Best lsp for C](https://www.reddit.com/r/neovim/comments/1fxfcnz/best_lsp_for_c/) 
	- [ ] Someone mentions [Autotools](https://en.wikipedia.org/wiki/GNU_Autotools) 
- [ ] [How to use clangd C/C++ LSP in any project](https://gist.github.com/Strus/042a92a00070a943053006bf46912ae9) 
- [ ] [clangd Documentation](https://clangd.llvm.org/) [Github](https://github.com/clangd/clangd) 
- [ ] [Github issue about header handling in clangd](https://github.com/clangd/clangd/issues/1534) 
- [ ] [LSP Devtools](https://lsp-devtools.readthedocs.io/en/latest/) A python pip package that can help diagnose LSP traffic between client and server by running an "agent" in-between the two
	- [ ] `python -m venv [path]`: Create a python virtual environment in a particular folder. Once created the python and pip binaries are available inside a `bin` folder in that folder. Installing pip packages is allowed (whereas the regular python environment is managed by `apt` and installing things through pip directly is disallowed). Packages installed in the virtual environment are only available inside that environment.
	- [ ] Inside my LSP-clangd options I did the following:
```json
{
	"binary": "custom",
	"initializationOptions": {
		"custom_command": [ "/home/robbitay/my_stuff/python_env/bin/lsp-devtools", "agent", "--", "/home/robbitay/.cache/sublime-text/Package Storage/LSP-clangd/clangd_21.1.8/bin/clangd" ],
	},
}
```
- [ ] [compdb](https://github.com/Sarcasm/compdb) command line tool to manipulates compilation databases (pip python package)
	- [ ] `pyton -m venv [path]`, `cd [path]/bin`, `./pip install compdb`, `./compdb -p [path/to/project] list > [path/to/new_compile_commands.json]`
- [ ] 