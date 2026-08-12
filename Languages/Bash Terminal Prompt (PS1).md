- [ ] In `~/.bashrc` there is an environment variable that gets set called `PS1` that determines the format of the input prompt you get in all terminals. This file holds notes about the syntax for that terminal prompt format string
- [ ] `PS1` stands for *Prompt String 1*
- [ ] [Bash/Prompt Customization - Arch Linux Wiki](https://wiki.archlinux.org/title/Bash/Prompt_customization)
- [ ] Color changing escape sequences need to be surrounded in square brackets in order to keep the terminal from advancing the cursor. Square brackets need to be escaped in bash strings
- [ ] `color_prompt` is set to `yes` or `[blank]` based on output of `xterm-color`
- [ ] My preferred colored prompt:
```bash
PS1='${debian_chroot:+($debian_chroot)}\[\033[7m\033[01;32m\]\h\[\033[00m\]:\[\033[7m\033[01;34m\]\w\[\033[00m\] ➜ '
```
![[ColoredPromptSnippetMonokaiTilix.png]]
- [ ] My preferred uncolored prompt:
```bash
PS1='${debian_chroot:+($debian_chroot)}\h:\w ➜ '
```
![[UncoloredPromptSnippetMonokaiTilix.png]]
- [ ] Default Colored Prompt `PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '`
- [ ] Default Uncolored Prompt `PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '`
- [ ] 

---
# Special Escape Sequences
[Arch Linux Man Page](https://man.archlinux.org/man/bash.1#PROMPTING)
- [ ] `\h`: Hostname up to first `.` (aka computer name). Example: `LubuntuLaptop`
- [ ] `\H`: Full Hostname
- [ ] `\w`: Current Working Directory (aka `$PWD`). Example: `~/my_stuff/programs`
- [ ] `\W`: Current folder name. Example: `my_stuff`
- [ ] `\u`: Username. Example: `robbitay`
- [ ] `\d`: Current Date. Example: `Sun Jan 18`
- [ ] `\t`: Current Time 24hr format. Example: `13:38:20`
- [ ] `\T`: Current Time 12hr format. Example: `01:38:20`
- [ ] `\@`: Current time in 12hr AM/PM format. Example: `09:12 AM`
- [ ] `\A`: Short Current Time. Example: `17:35`
- [ ] `\!`: History number of the current command. Example: `151`
- [ ] `\#`: Command number of the current command. Example: `2`