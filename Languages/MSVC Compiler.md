## Notes
- [ ] Compiler version: **v19.41.34120**
- [ ] Install Location: `C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.41.34120/bin/Hostx64/x64/cl.exe`
## CLI Options [Link](https://learn.microsoft.com/en-us/cpp/build/reference/compiler-options-listed-alphabetically?view=msvc-170)
- [ ] `/P` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/p-preprocess-to-a-file?view=msvc-170): Preprocess the input file(s) and output the result to a .i file(s) with the same name as the input (use with `/C` to preserve comments)
- [ ] `/C` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/c-preserve-comments-during-preprocessing?view=msvc-170): Preserve comments through the preprocessor, requires `/E`, `/P`, or `/EP` options to be present
- [ ] `/PD`: Print all macro definitions to stdout (probably want to use `>` to save result to a file)
- [ ] `/FA`/`/Fa` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/fa-fa-listing-file?view=msvc-170): Output/Configure a listing file containing assembler code
- [ ] `/Fm` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/fm-name-mapfile?view=msvc-170): Output a map file with a specified name, containing information about where each section of the assembly code was placed during the linking process
- [ ] `/Fe` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/fe-name-exe-file?view=msvc-170): Set the output exe file path
- [ ] `/Fo` [Link](https://learn.microsoft.com/en-us/cpp/build/reference/fo-object-file-name?view=msvc-170): Set the output object file path