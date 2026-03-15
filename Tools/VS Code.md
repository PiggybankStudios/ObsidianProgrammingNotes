## Notes
- [ ] I have v1.58.0 but updated to v1.100.2 on June 2nd 2025. I had to set the "Update" option to "Manual" in VS Code settings
- [ ] `.code-workspace` file can be created to allow changing of settings and configuration of a project beyond just using a particular folder as the project root
- [ ] Turning off Codelens removes the half-line information displays that I hate
- [ ] VS Code settings are saved at `%APPDATA%/Roaming/Code/User/settings.json` and `keybindings.json`
- [ ] 
## Hotkeys
- [ ] `Alt+O`: Switch scene/script (godot-tools)
## Extensions
- [ ] **godot-tools** [Link](https://marketplace.visualstudio.com/items?itemName=geequlim.godot-tools) [Github](https://github.com/godotengine/godot-vscode-plugin)
- [ ] **C# Tools for Godot** [Link](https://marketplace.visualstudio.com/items?itemName=neikeq.godot-csharp-vscode) [Github](https://github.com/godotengine/godot-csharp-vscode)
- [ ] 

# Extension Development
- [ ] **See** [[Node.js and npm]] for language and file-structure related notes that are sort of VS Code related but more about the languages and tooling
- [ ] [Your First Extension](https://code.visualstudio.com/api/get-started/your-first-extension) 
	- [ ] Generate a new VS Code Extension with *Yeoman*: `npx --package yo --package generator-code -- yo code`
	- [ ] [Extension Guidelines](https://code.visualstudio.com/api/references/extension-guidelines) 
	- [ ] [Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown) 
	- [ ] [Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/) 
- [ ] [Github - Taylors Tools Extension](https://github.com/PiggybankStudios/TaylorsToolsExtension) 
- [ ] [Publishing Extension](https://code.visualstudio.com/api/working-with-extensions/publishing-extension) 
	- [ ] Install `vsce` -> `npm install -g @vscode/vsce`(might need `sudo` to create `/usr/local/lib/node_modules`), depends on 299 packages
	- [ ] Then you can do `vsce package` to create `.vsix` file or `vsce publish`
	- [ ] Current *vsce* = **v3.7.1**
	- [ ] `vsce` Commands:
```
Commands:
  ls [options]                       Lists all the files that will be published/packaged
  package|pack [options] [version]   Packages an extension
  publish [options] [version]        Publishes an extension
  unpublish [options] [extensionid]  Removes an extension from the marketplace. Example extension id: ms-vscode.live-server.
  generate-manifest [options]        Generates the extension manifest from the provided VSIX package.
  verify-signature [options]         Verifies the provided signature file against the provided VSIX package and manifest.
  ls-publishers                      Lists all known publishers
  delete-publisher <publisher>       Deletes a publisher from marketplace
  login <publisher>                  Adds a publisher to the list of known publishers
  logout <publisher>                 Removes a publisher from the list of known publishers
  verify-pat [options] [publisher]   Verifies if the Personal Access Token or Azure identity has publish rights for the publisher
  show [options] <extensionid>       Shows an extension's metadata
  search [options] <text>            Searches extension gallery
  help [command]                     display help for command
```
- [ ] `vsce package` runs `npm run package` which runs the `"package"` npm script in `package.json` which is: `webpack --mode production --devtool hidden-source-map`?
- [ ] For some reason, on the first boot of VS Code it thinks that the webpack *watcher* never exits, but if we select *Debug Anyway* then it works forever more
- [ ] ==TODO:== Ne== I need to get my extension to be compatible with VS Code **v1.106.2026021002** 
- [ ] 