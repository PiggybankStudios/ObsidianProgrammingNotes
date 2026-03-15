## Notes
- [ ] Debian packages: `npm` and `nodejs`
	- [ ] Linux versions as of March 8th 2026 - Node.js **v20.19.4** Npm **v9.2.0**
	- [ ] Windows versions as of March 8th 2026 - Node.js **v24.14.0** Npm **v11.9.0** (installed via .msi from [nodejs.org](https://nodejs.org/en/download))
- [ ] `npx` runs an npm package as a tool
- [ ] `package.json` is what defines the package in the current folder and tells npm about dependencies
- [ ] Dependencies can be cached in a global folder at `/usr/local/lib/node_modules?` or `%APPDATA%\npm\node_modules` or cached in a local `node_modules` folder. Configure this by doing `TODO:`
- [ ] ==TODO:== *npm scripts* can be used to do what? Is it just defining custom "commands" that can be run with `npm run [command]` while in that package's folder?
- [ ] `jsconfig.json` is used for Javascript engine configuration, `tsconfig.json` is the Typescript equivalent. Example `tsconfig.json`:
```json
{
	"compilerOptions": {
		"module": "Node16",
		"target": "ES2022",
		"lib": [
			"ES2022"
		],
		"sourceMap": true,
		"rootDir": "src",
		"strict": true,   /* enable all strict type-checking options */
		/* Additional Checks */
		// "noImplicitReturns": true, /* Report error when not all code paths in function return a value. */
		// "noFallthroughCasesInSwitch": true, /* Report errors for fallthrough cases in switch statement. */
		// "noUnusedParameters": true,  /* Report errors on unused parameters. */
	}
}
```
- [ ] *Node Version Manager* aka `nvm` [Github](https://github.com/nvm-sh/nvm) (not directly supported on Windows)
- [ ] [npm registry](https://www.npmjs.com/) 
- [ ] 

### **Webpack** javascript bundler
- [ ] Install webpack through npm: `npm install --global webpack` (also `webpack-cli`)
- [ ] [How to use webpack for VS Code Extension](https://code.visualstudio.com/api/working-with-extensions/bundling-extension#using-webpack) 
	- [ ] `npm i --save-dev webpack webpack-cli`
	- [ ] `npm i --save-dev ts-loader`
- [ ] Configure webpack with `webpack.config.js`
- [ ] Scripts:
```json
"compile": "webpack --mode development"
"watch": "webpack --mode development --watch"
"vscode:prepublish": "npm run package"
"package": "webpack --mode production --devtool hidden-source-map"
```
- [ ] Commands:
```
  build|bundle|b [entries...] [options]  Run webpack (default command, can be omitted).
  configtest|t [config-path]             Validate a webpack configuration.
  help|h [command] [option]              Display help for commands and options.
  info|i [options]                       Outputs information about your system.
  serve|server|s [entries...]            Run the webpack dev server and watch for source file changes
                                         while serving. To see all available options you need to install 'webpack', 'webpack-dev-server'.
  version|v [options]                    Output the version number of 'webpack', 'webpack-cli' and
                                         'webpack-dev-server' and commands.
  watch|w [entries...] [options]         Run webpack and watch for files changes.
```
- [ ] 

### **Yeoman** project generator
- [ ] Used by VS Code to create a new extension project
- [ ] `npx --package yo --package generator-code -- yo code` to generate VS Code extension from Yeoman template named `generator-code` [NPM Link](https://www.npmjs.com/package/generator-code) 
- [ ] 

### **VS Code** extensions
- [ ] In `.vscode/launch.json` the run extension launch mode has `"preLaunchTask": "${defaultBuildTask}"` which runs first task in `.vscode/tasks.json` which is `npm watch` which is defined in `package.json` to be `webpack --watch`
- [ ] There's also `npm watch-tests` which is part of the `"build"` group but not the default task and runs `tsc -p . -w --outDir out`
- [ ] 