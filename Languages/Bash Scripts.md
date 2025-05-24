## Notes
- [ ] `#!/bin/bash` at the top of the file (NOT `#!/bin/sh`!)
- [ ] Make a folder if it doesn't already exist with `-p` flag on mkdir: `mkdir -p _build`
- [ ] `if [ $something -eq 1 ]` spaces matter between `[ ]`
- [ ] Delete a file with `rm` delete a folder with `rm -r`
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
- [ ] 