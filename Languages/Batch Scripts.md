## Notes
- [ ] `REM` and `::` can both be used as a pseudo comment syntax. However, `::` doesn't seem work properly when inside an `if ()`/`else ()` block
- [ ] `if "%VAR%"=="1" ( ... ) else ( ... )` <- if/else syntax. Note that `(` must be on same name as `if`/`else`
- [ ] `if not exist build mkdir build` <- Create a folder if it doesn't exist already
- [ ] `%time%` format `16:21:50.97`
- [ ] `set` [Link](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set_1) Sets an environment variable. Use `/a` to have the value numerically evaluated
- [ ] [SS64](https://ss64.com/nt/)
- [ ] When setting variables inside an `if ( ... )` scope or a `for ... do ( ... )` scope you'll find that it does not work as you expect. The value that you set for any variable does not take affect until after the scope exits. So a write followed by a read from a variable will not work well. In order to get around this you can add the following line to the top of your batch file `setlocal enabledelayedexpansion` and then use `!VARIABLE_NAME!` syntax instead of `%VARIABLE_NAME%` when you want to read the value of a variable from within a loop. This works by "delaying the expansion" of the variable into a value until the line is actually executed (since blocks get read in with some sort of lookahead I guess?) so the write to the value within the scope affects the read from the value later in the scope. [StackOverflow Link](https://stackoverflow.com/questions/6679907/how-do-setlocal-and-enabledelayedexpansion-work)
- [ ] For some reason a single line `IF` block that sets a variable doesn't always work properly. Maybe the syntax for `SET` is consuming the closing parenthesis for the RHS of the assignment?
- [ ] 