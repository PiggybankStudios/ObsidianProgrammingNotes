# Notes
- [ ] Bought MacBook Pro on **March 22nd 2026** for *$1,699* (with *$99* magic mouse, total after tax *$1,972.17*) from Bellevue Square Mall Apple Store (return by Apr 5th)
	- [ ] **Model**: 14-inch MacBook Pro - Space Black MBP 14 SB/10C/10C GPU/16GB/1TB-USA
	- [ ] **CPU**: M5 
	- [ ] **Screen**: 14" 1800x1169
	- [ ] **Part Number**: MDE14LL/A
	- [ ] **Serial Number**: H2YR91WV24
	- [ ] **Color**: Space Black
	- [ ] **Warrany Expires**: March 21st 2027
	- [ ] **OSX Version**: 26.3.1 *Tahoe*
- [ ] Couldn't sign-in to Apple account with password during bootflow
- [ ] Updated to **MacOS 26.3.1 Tahoe** during bootflow
- [ ] Enable color in Terminal/zsh and change prompt by adding the following to `~/.zshrc`:
```
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
export PROMPT='%F{green}%n%f %B%F{240}%~%f%b %(!.#.$) '
```
- [ ] Running something like `clang` in Terminal launches a prompt that installed CLI developer tools (related to XCode?) into `Library/Developer/CommandLineTools/usr/bin`
- [ ] Clang Version: *Apple Clang 17.0.0*
- [ ] Python Version: *3.9.6*
- [ ] Swift Version: *6.2.4* (Driver: *1.127.15*)
- [ ] Git Version: *2.50.1* (Apple Git-155)
- [ ] *zsh* is default shell on OSX since Catalina - [Bash vs Zsh](https://blog.logrocket.com/bash-vs-zsh/) 
- [ ] Default difftool for git requires XCode install:
      `xcode-select: error: tool 'opendiff' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance`
- [ ] XCode license is at `/Applications/Xcode.app/Contents/Resources/en.lproj/License.rtf` had to run `sudo xcodebuild -license` before git would work again
- [ ] `xcode-select --install` Install XCode on a new OSX install?
- [ ] To install CMake for command-line use after installing the Cmake.app from the .dmg [on their site](https://cmake.org/download/), I had to run `sudo "/Applications/CMake.app/Contents/bin/cmake-gui" --install` (See *Tools*->*How to Install for Command Line Use* in the GUI app)
- [ ] Installed **ninja 1.13.2** ([[Ninja Notes]]) by downloading [mac binary](https://github.com/ninja-build/ninja/releases/tag/v1.13.2) (in .zip) and putting into `~/.local/bin/ninja` and handling the Mac quarantine behavior (Opening System Settings after first trying to launch and selecting Allow in the Security section and then running again and putting in password/fingerprint)
- [ ] To run an app bundle we can use `open MyApp.app` but we then don't get stdout from `print` calls. We can try `open -a MyApp.app` to open a terminal that then opens the app but this doesn't work for me (Maybe requires calling `NSLog`?).Instead we can just run the binary straight out of the app, like `cd MyApp.app/Contents/MacOS/` and then run the binary like normal `./my_app`.
- [ ] You can unpack a .pkg file by doing ` pkgutil --expand-full something.pkg`
- [ ] To install Android SDK Platform Tools I ran `brew install --cask android-platform-tools` which installed it into `/opt/homebrew/bin/` 
- [ ] You can open an app by name from shell by doing: `open -a [app_name]`
- [ ] 
## Hotkeys
### Global
- [ ] **⌘+Opt+Escape** - Force Quit Menu
- [ ] **⌘+Space** - Spotlight
- [ ] **⌘+Q** - Quit Application
- [ ] **⌘+Ctrl+Q** - Lock
- [ ] **⌘+Space** - Spotlight
- [ ] **⌘+Left/Right** - Home/End equivalent (most text editing) (**Fn+Left/Right** also seems to work sometimes)
- [ ] **Opt+Left/Right** - Move by words (most text editing)
- [ ] **Ctrl+Up** - Mission Control
- [ ] **Ctrl+Down** - Application Windows
- [ ] **Ctrl+Left/Right** - Change workspace left/right
- [ ] **Opt+LeftClickDrag** - Tile window
- [ ] **F11** - Show Desktop
- [ ] **⌘+Shift+3/4** - Screenshot Screen/Region (Hit spacebar when capturing region to switch to capturing Window)
- [ ] **⌘+Ctrl+F** = Fullscreen application
- [ ] **⌘+M** = Minimize
- [ ] **Fn+Ctrl+C** = Center window
- [ ] **Ctrl+F2** = Focus topbar
### Finder
- [ ] **⌘+Shift+.** - Show hidden files
- [ ] **⌘+Shift+H** - Goto Home Folder
- [ ] **⌘+Shift+C** - Goto Mac Root
- [ ] **⌘+Up** - Goto parent folder
- [ ] **⌘+Delete** - Move to Trash
### Terminal
- [ ] **⌘+K** - Clear screen
- [ ] **Ctrl+A/E** - Home/End
### Chrome
- [ ] **⌘+LeftClick** - Open link in new tab
- [ ] **Option+LeftClick** - Download link
- [ ] 

# TODO
---
- [x] Can we get the key hold repeat speed to be faster?
	- [x] Repeat = max, delay = max-1
- [x] Should we install another terminal GUI and/or shell besides the one that's installed by default?
	- [ ] Key repeat fine now
	- [ ] zsh seems good
	- [ ] **Home/End** is biggest annoyance but **Control+A/E** do work
- [ ] Go through pre-installed software and remove things that I don't need or require subcriptions
- [x] How do I type Command/Control/Option icons?
	- [ ] [Link](https://apple.stackexchange.com/questions/4074/what-do-i-type-to-produce-the-command-symbol-in-mac-os-x) 
	- [ ] ⌘ is called *Place of Interest* in Emoji menu
- [ ] Can I remove delay for keyboard/mouse input while waiting for spaces change animation to complete?
- [ ] How to I **Cut**/**Paste** files in Finder?
- [ ] How do we customize Ghostty?
- [ ] 

# Applications
---
## Added
- [x] Obsidian
- [x] Google Chrome
	- [x] Kagi Extension
- [x] Clang - Devoloper Command-Line Tools
- [x] Python - Devoloper Command-Line Tools
- [x] Ghostty [Link](https://ghostty.org/) 
- [x] KeePass GUI
	- [ ] [KeePassium](https://apps.apple.com/us/app/keepassium-keepass-passwords/id1435127111) (Pro is $80 one time purchase)
	- [ ] [KeePass Password Manager](https://apps.apple.com/us/app/keepass-password-manager/id6461546929) 
	- [x] [Strongbox - Password Manager](https://apps.apple.com/us/app/strongbox-password-manager/id897283731) (Pro is $100, only on OSX and iOS)
- [x] Sublime Text (bought new license)
- [x] Sublime Merge
- [x] Discord
- [x] Revolt? PWA? - https://chat.handmadecities.com works fine
- [ ] VS Code
- [ ] GIMP?
- [x] Homebrew [Link](https://brew.sh/) 
	- [ ] `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
	- [ ] The add to `~/.zprofile` by doing `echo >> /Users/robbitay/.zprofile` and `echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> /Users/robbitay/.zprofile`
- [x] XCode (installed from AppStore)
- [x] `lsd` (also installed `eza` instead, both through homebrew)
- [x] micro (through homebrew)
- [ ] [Mos](https://mos.caldis.me/) or [Mac Mouse Fix](https://macmousefix.com/en/) ?
- [ ] Finder Alternative:
	- [ ] [Forklift4](https://binarynights.com/) 
	- [ ] [PathFinder](https://cocoatech.io/) 
	- [ ] [QSpace](https://qspace.awehunt.com/en-us/index.html) 
	- [ ] [Folders File Manager](https://foldersapp.dev/) 
	- [ ] [SpaceDrive](https://spacedrive.com/) [Github](https://github.com/spacedriveapp/spacedrive) 
	- [ ] [Commander One](https://commander-one.com/) 
- [ ] Google Drive?
- [x] Local Send (in AppStore)
- [x] FiraCode Nerd Font (install through Font Book app)
- [ ] Terminal Click
- [x] Fred No OSX version yet
- [x] nnd? Doesn't work on OSX
- [ ] jai compiler
- [ ] zig compiler?
- [x] Godot?
- [x] .NET SDK 10
- [ ] lazygit?
## Removed
- [ ] 

# Settings
---
- [ ] *General*
	- [ ] *About* -> Name = `TaylorsMac`
- [ ] *Appearance*
	- [ ] Appearance = Dark
	- [ ] Liquid Glass = Tinted
	- [ ] ==TODO== Show scrollbars = Always?
	- [ ] Click in the scrollbar to = Jump to the spot that's clicked
- [ ] *Desktop and Dock*
	- [ ] Minimize Windows into application icon = True
	- [ ] Show suggested and recent apps in dock = False
	- [ ] Click wallpaper to show Desktop = Only in Stage Manager
	- [ ] Default Web Browser = Google Chrome
	- [ ] Automatically rearrange Spaces based on most recent use = False
	- [ ] Hot Corners -> Bottom Right -> None (used to be Quick Note)
	- [ ] ==TODO== Close windows when quitting an application = False?
	- [ ] ==TODO== Displays have separate Spaces = False?
- [ ] *Notifications*
	- [ ] Game Center = Off
	- [ ] Home = Off
	- [ ] Tips = Off
- [ ] *Sound*
	- [ ] Alert Sound = Pluck
- [ ] *Displays*
	- [ ] Advanced -> Show resolutions as list = True
	- [ ] Resolution = 1800x1169
- [ ] *Menu Bar*
	- [ ] Menu Bar Controls -> Bluetooth = Enabled
	- [ ] Menu Bar Controls -> Keyboard Brightness = Enabled
- [ ] *Spotlight*
	- [ ] Show Related Content = False
	- [ ] Help Apple Improve Search = False
	- [ ] Results from Apps -> Tips = False
- [ ] *Lock Screen*
	- [ ] Turn displays off on battery when inactive = For 30 minutes
	- [ ] Turn displays off on power adapter when inactive = For 2 hours
	- [ ] Require password after screen saver begins or display is turned off = Never
- [ ] *Privacy and Security*
	- [ ] Location Services = Off
	- [ ] Apple Intelligence Report = Off
- [ ] *Keyboard*
	- [ ] Key repeat rate = Fast
	- [ ] Delay until repeat = Short-1
	- [ ] Keyboard brightness = Max
	- [ ] Keyboard backlight off after = 5 minutes
	- [ ] *Keyboard Shortcuts*... -> *Function Keys* -> Use F1, F2, etc. keys as standard function keys = True
	- [ ] *Keyboard Shortcuts* -> *Mission Control* -> *MissionControl* -> *Move left/right a space* = **Ctrl+Option+Left/Right**
	- [ ] *Input Sources Edit...* -> Show input menu in menu bar
	- [ ] *Text Input* -> *Edit...* -> *Add period with double-space* = **False** 
- [ ] *Mouse*
	- [ ] Secondary Click = Click Right Side
- [ ] *Trackpad*
	- [ ] Force Click and haptic feedback = False
	- [ ] ==TODO== Tap to click = True?