## Notes
- [ ] Settings are saved in `~/.config/micro/`
- [ ] Can create an `init.lua` in the config folder to create a single file plugin named `initlua`
- [ ] Example `init.lua`:
```lua
local config = import("micro/config")
local shell = import("micro/shell")

function init()
    -- true means overwrite any existing binding to Ctrl-r
    -- this will modify the bindings.json file
    config.TryBindKey("Ctrl-r", "lua:initlua.gorun", true)
end

function gorun(bp)
    local buf = bp.Buf
    if buf:FileType() == "go" then
        -- the true means run in the foreground
        -- the false means send output to stdout (instead of returning it)
        shell.RunInteractiveShell("go run " .. buf.Path, true, false)
    end
end
```
- [ ] 
## Keybindings
- [ ] **Ctrl+G**/**F1**: Help menu (or **F1**)
- [ ] **Alt+G**: Toggle display of short list of useful keybindings
- [ ] **Ctrl+Q**/**F4**/**F10**: Close Buffer (aka "quit")
- [ ] **Ctrl+S**/**F2**: Save
- [ ] **Ctrl+O**: Open
- [ ] **Ctrl+E**: Command bar
- [ ] **Ctrl+Z**/**Ctrl+Y**: Undo/Redo
- [ ] **Ctrl+F**/**F3**/**F7**: Find (**Ctrl+N**: goto next match, **Ctrl+P**: goto previous match)
- [ ] **Ctrl+D**: Duplicate line
- [ ] **Ctrl+K**: Cut line
- [ ] **Ctrl+T**: New tab (Use **Alt+<**/**Alt+>** to move between tabs)
- [ ] **Ctrl+W**: Cycle through buffers (panes) in the current tab
- [ ] **Alt+{**/**Alt+}**: Goto beginning/end of file (like **Ctrl+Home**/**Ctrl+End**)
- [ ] **Alt+A**/**Alt+E**: Goto end/beginning of line (same as **Home**/**End**)
- [ ] **Ctrl+L**: Jump to line number
- [ ] **Alt+Backspace**: Delete word left of cursor
- [ ] **Shift+Tab**: Decrease indent on current line(s)
- [ ] **Ctrl+U**: Toggle macro recording (**Ctrl+J** runs latest macro)
- [ ] **Ctrl+LeftMouse**: Add cursor (multi-cursor)
- [ ] **Alt+M**: Spawn multiple cursors, one for each line in selection
- [ ] **Ctrl+H**: Backspace alternative
- [ ] **Ctrl+R**: Toggle line numbers
- [ ] **Alt+F**/**Alt+B**: Next/Previous word (same as **Ctrl+Right**/**Ctrl+Left**)
- [ ] 
## Commands - **Ctrl+E**
- [ ] **Tab**: List commands (same as `help commands`) or autocomplete
- [ ] `help defaultkeys`: List of default keybindings
- [ ] `help keybindings`: List of current keybindings
- [ ] `help tutorial`: A brief tutorial that gives you overview of all the other help functions
- [ ] `help options`: Gives a list of all the options you can customize
- [ ] `help plugins`: Explains how micro's plugin system works and how to create your own
- [ ] `set <option> <value>`: Set an option globally
- [ ] `setlocal <option> <value>`: Set option for current buffer
- [ ] `set colorscheme <value>`: Change the editor color scheme (see `help colors`)
- [ ] `vsplit/hsplit <filename>`: Split the editor vertically/horizontally and open `<filename>` in bottom/right pane
- [ ] `bind <key> <action>`: Bind a hotkey to `<action>` (for this session only)
- [ ] `raw`: Show what keys are being received by Micro from the terminal emulator
- [ ] `pwd`: Print current working directory ==TODO:== Is this just a normal linux command?
## Actions
- *All Possible Actions*:
	- [ ] `CursorUp`
	- [ ] `CursorDown`
	- [ ] `CursorPageUp`
	- [ ] `CursorPageDown`
	- [ ] `CursorLeft`
	- [ ] `CursorRight`
	- [ ] `CursorStart`
	- [ ] `CursorEnd`
	- [ ] `SelectToStart`
	- [ ] `SelectToEnd`
	- [ ] `SelectUp`
	- [ ] `SelectDown`
	- [ ] `SelectLeft`
	- [ ] `SelectRight`
	- [ ] `SelectToStartOfText`
	- [ ] `SelectToStartOfTextToggle`
	- [ ] `WordRight`
	- [ ] `WordLeft`
	- [ ] `SubWordRight`
	- [ ] `SubWordLeft`
	- [ ] `SelectWordRight`
	- [ ] `SelectWordLeft`
	- [ ] `SelectSubWordRight`
	- [ ] `SelectSubWordLeft`
	- [ ] `MoveLinesUp`
	- [ ] `MoveLinesDown`
	- [ ] `DeleteWordRight`
	- [ ] `DeleteWordLeft`
	- [ ] `DeleteSubWordRight`
	- [ ] `DeleteSubWordLeft`
	- [ ] `SelectLine`
	- [ ] `SelectToStartOfLine`
	- [ ] `SelectToEndOfLine`
	- [ ] `InsertNewline`
	- [ ] `InsertSpace`
	- [ ] `Backspace`
	- [ ] `Delete`
	- [ ] `Center`
	- [ ] `InsertTab`
	- [ ] `Save`
	- [ ] `SaveAll`
	- [ ] `SaveAs`
	- [ ] `Find`
	- [ ] `FindLiteral`
	- [ ] `FindNext`
	- [ ] `FindPrevious`
	- [ ] `DiffPrevious`
	- [ ] `DiffNext`
	- [ ] `Undo`
	- [ ] `Redo`
	- [ ] `Copy`
	- [ ] `CopyLine`
	- [ ] `Cut`
	- [ ] `CutLine`
	- [ ] `DuplicateLine`
	- [ ] `DeleteLine`
	- [ ] `IndentSelection`
	- [ ] `OutdentSelection`
	- [ ] `OutdentLine`
	- [ ] `IndentLine`
	- [ ] `Paste`
	- [ ] `SelectAll`
	- [ ] `OpenFile`
	- [ ] `Start`
	- [ ] `End`
	- [ ] `PageUp`
	- [ ] `PageDown`
	- [ ] `SelectPageUp`
	- [ ] `SelectPageDown`
	- [ ] `HalfPageUp`
	- [ ] `HalfPageDown`
	- [ ] `StartOfLine`
	- [ ] `EndOfLine`
	- [ ] `StartOfText`
	- [ ] `StartOfTextToggle`
	- [ ] `ParagraphPrevious`
	- [ ] `ParagraphNext`
	- [ ] `SelectToParagraphPrevious`
	- [ ] `SelectToParagraphNext`
	- [ ] `ToggleHelp`
	- [ ] `ToggleDiffGutter`
	- [ ] `ToggleRuler`
	- [ ] `JumpLine`
	- [ ] `ResetSearch`
	- [ ] `ClearInfo`
	- [ ] `ClearStatus`
	- [ ] `ShellMode`
	- [ ] `CommandMode`
	- [ ] `Quit`
	- [ ] `QuitAll`
	- [ ] `AddTab`
	- [ ] `PreviousTab`
	- [ ] `NextTab`
	- [ ] `NextSplit`
	- [ ] `Unsplit`
	- [ ] `VSplit`
	- [ ] `HSplit`
	- [ ] `PreviousSplit`
	- [ ] `ToggleMacro`
	- [ ] `PlayMacro`
	- [ ] `Suspend (Unix only)`
	- [ ] `ScrollUp`
	- [ ] `ScrollDown`
	- [ ] `SpawnMultiCursor`
	- [ ] `SpawnMultiCursorUp`
	- [ ] `SpawnMultiCursorDown`
	- [ ] `SpawnMultiCursorSelect`
	- [ ] `RemoveMultiCursor`
	- [ ] `RemoveAllMultiCursors`
	- [ ] `SkipMultiCursor`
	- [ ] `None`
	- [ ] `JumpToMatchingBrace`
	- [ ] `Autocomplete`