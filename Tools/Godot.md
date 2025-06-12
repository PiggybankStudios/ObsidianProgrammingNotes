## Versions
- [ ] v4.4.1
- [ ] v4.4-stable_mono_win64
	- Cartomantic
- [ ] v4.1.2-stable_mono_win64
- [ ] v4.2.2-stable
- [ ] v4.2.1-stable_mono_win64
- [ ] v3.4.4-stable
- [ ] v3.1.1-stable
## Notes
- [ ] UID Caching Issue
	- [ ] [Issue: Some resources will randomly reset their UID](https://github.com/godotengine/godot/issues/62258)
	- [ ] [chore: add UID cache](https://github.com/AlexInABox/grow-green/pull/237) - [Comment](https://github.com/godotengine/godot/issues/62258#issuecomment-2082956521)
- [ ] [Issue about Tooltips on Exported Properties in C#](https://github.com/godotengine/godot-proposals/issues/8269)
- [ ] Adding a button to the Inspector panel for a Tool script:
```csharp
[ExportToolButton(text: "Display String")]
Callable DisplayString => Callable.From(() => { /* ... */ });
```
- [ ] [Godot Editor Icons](https://godot-editor-icons.github.io/)
- [ ] 
## Hotkeys
- [ ] `Shift+F12`: Expand Bottom Panel to Top of Screen
- [ ] `Alt+N`: Toggle Animation Bottom Panel
- [ ] `Alt+A`: Toggle Audio Bottom Panel
- [ ] `Alt+D`: Toggle Debugger Bottom Panel
- [ ] `Alt+F`: Toggle FileSystem Bottom Panel
- [ ] `Alt+O`: Toggle Output Bottom Panel
- [ ] `Alt+S`: Toggle Shader Bottom Panel
- [ ] `Ctrl+J`: Toggle Last Opened Bottom Panel
- [ ] `F12`: Continue (while debugging)
- [ ] `Alt+B`: Build Project (C#/Mono)
- [ ] `F5`: Run Project (`Ctrl+Shift+F5`: Run Specific Scene)
- [ ] `F6`: Run Current Scene
- [ ] `F7`: Pause Running Project
- [ ] `F8`: Stop Running Project
- [ ] `Ctrl+Alt+K`: Clear Debug Output
- [ ] `Ctrl+Alt+P`: Command Palette (was `Ctrl+Shift+P`)
- [ ] `Ctrl+Shift+F11`: Distraction Free Mode
- [ ] `Ctrl+F1/F2/F3/F4/F5`: Open 2D Editor / 3D Editor / Script Editor / Game View / Asset Library
- [ ] `F1`: Search Help
- [ ] `Ctrl+Alt+P`: Search in FileSystem
- [ ] `Shift+F11`: Toggle Fullscreen
- [ ] `Ctrl+P`: Quick Open
- [ ] `Ctrl+Shift+O`: Quick Open Scene
- [ ] `Ctrl+Alt+O`: Quick Open Script
- [ ] `Ctrl+Shift+T`: Reopen Closed Scene
- [ ] `Ctrl+F12`: Take Screenshot
- [ ] `Ctrl+Alt+E`: Open in External Program (FileSystem Panel)
- [ ] `Ctrl+Alt+T`: Open in Terminal (FileSystem Panel)
- [ ] `Ctrl+Alt+R`: Open in File Manager (FileSystem Panel)
- [ ] `Ctrl+Shift+C`: Copy Path (FileSystem Panel)
- [ ] `Ctrl+A`: Add a Child Node (Scene Panel)
- [ ] `Ctrl+1/2/3/4`: Switch to 1/2/3/4 Viewport Layout (Hold `Alt` for alternate options on 2 and 3)
- [ ] `F`: Focus on Selected Item
- [ ] `O`: Focus on Origin
- [ ] `Shift+F`: Toggle Freelook
- [ ] `PageDown`: Snap Object to Floor
- [ ] `Ctrl+P`: Toggle Camera Preview