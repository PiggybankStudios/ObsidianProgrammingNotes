## Notes
- [ ] `#!/bin/bash` at the top of the file (NOT `#!/bin/sh`!)
- [ ] Make an `.sh` file executable with `chmod +x [filename].sh`
- [ ] Comments start with `#` symbol
- [ ] Environment variables set like `ProjectName="Test Project"` or `RunProgram=1`
- [ ] Make a folder if it doesn't already exist with `-p` flag on mkdir: `mkdir -p _build`
- [ ] `if [ $something -eq 1 ]` spaces matter between `[ ]`
	- [ ] Comparison operators: `-eq`, `-gt`, `-lt`, `-ne`
- [ ] Double square-brackets around if condition is available in bash/kornshell specifically
- [ ] Delete a file with `rm` delete a folder with `rm -r`
- [ ] Get result of last run command with `$?`
- [ ] Store output of command in variable using backticks or `${ }`: ```
```
variable=`command`
or
variable=${command}
```
- [ ] Check if a variable matches a regular expression with:
```bash
if [[ "$variable" =~ regex_pattern ]]; then
    ...
fi
```
- [ ] Get the current working directory: `echo $PWD`
- [ ] `if` statements do not need a `;` following the `]` if the `then` keyword is on the next line
- [ ] 