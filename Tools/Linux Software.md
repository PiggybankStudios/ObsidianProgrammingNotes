This file is a list of all of the software that we may install when setting up a Linux installation. Mostly acts like a checklist of things to do, but also a good place to keep notes about where each things is available from and in what form (as well as any quirks of installation/configuration)

- Update `~/.config/user-dirs.dirs` to change where things are saved
- Single command: `sudo apt install tilix git keepassxc lsd gimp micro clang kdiff3 make cmake`

## Always
---
#### Tilix
- Change to *FiraMono Nerd Font Regular* and *Monokai Dark* theme
- After first command it popped up a dialog about a VTE-related config issue https://gnunn1.github.io/tilix-web/manual/vteconfig/
- Update default terminal with `sudo update-alternatives --config x-terminal-emulator` (could need to add it manually with `sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/<your-term> 50`) (Some apps may read `xdg-mime default <your-term>.desktop x-scheme-handler/terminal`)
#### KeePassXC
- Apt/Debian Package Name: `keepassxc`
#### lsd
- Package Name: `lsd`
#### git
- Also `sudo apt-get install git-credential-oauth` and run `git credential-oauth configure`
- Update `~/.gitconfig` according to [[Git Config]] 
#### Obsidian
- Download AppImage version for Raspberry Pi. Made an `Obsidian.desktop` file in [[Raspberry Pi Notes]]
#### Sublime Text
##### dnf/rpm
- `sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg`
- `sudo dnf config-manager addrepo --from-repofile=https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo`
- `sudo dnf install sublime-text`
##### apt
- `wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo tee /etc/apt/keyrings/sublimehq-pub.asc > /dev/null`
- `echo -e 'Types: deb\nURIs: https://download.sublimetext.com/\nSuites: apt/stable/\nSigned-By: /etc/apt/keyrings/sublimehq-pub.asc' | sudo tee /etc/apt/sources.list.d/sublime-text.sources`
- `sudo apt-get update`
- `sudo apt-get install sublime-text` 
#### Sublime Merge
- Same as **Sublime Text** and then:
- `sudo apt-get install sublime-merge` or `sudo dnf install sublime-merge`
#### VLC
- Available in *Discover* store
#### GIMP
- Package name: `gimp`
#### micro
- Package name: `micro` 
#### nnd
#### clang
#### gcc
#### Eye of Gnome (eog)
- Maybe Gwenview instead?
#### KDiff3
#### Python
#### Dolphin
- Set to default file browser: `xdg-mime default org.kde.dolphin.desktop inode/directory`
- Fix "Open Terminal Here" options in Dolphin by editing `~/.config/kdeglobals`
```
[General]
TerminalApplication=tilix
TerminalService=com.gexperts.Tilix.desktop
```
#### curl


## Large but Useful
---
#### Firefox
#### Discord
(download .tar.gz, modify .desktop and copy into /usr/share/applications)
#### Spotify
Installed through Snap
#### Beyond Compare 4
#### Claude Desktop
- `sudo apt install curl gnupg`
- `sudo curl -fsSLo /usr/share/keyrings/claude-desktop-archive-keyring.asc https://downloads.claude.ai/claude-desktop/key.asc`
- `gpg --show-keys /usr/share/keyrings/claude-desktop-archive-keyring.asc`
- `echo "deb [arch=arm64 signed-by=/usr/share/keyrings/claude-desktop-archive-keyring.asc] https://downloads.claude.ai/claude-desktop/apt/stable stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list`
- `sudo apt update` and `sudo apt install claude-desktop`


## Maybe
---
#### lazygit
#### Snap
[Installing Snap on Fedora](https://snapcraft.io/docs/installing-snap-on-fedora) 
(created symlink from /snap 2.72-1)
#### make
#### cmake
#### Zig
#### Odin
#### Jai
#### qps
#### NeoVim
#### Emacs
#### Maven
#### Meson
#### gnupg
#### libsecret-tools
- Provides things like `secret-tool store --label=test test foo`
#### seahorse
- GUI for managing secrets and keyrings
#### Graphviz
#### Samba


## Handmade
---
#### C-Switch
#### Fred
#### Terminal Click


## Extensions and Plugins
---
#### UBlock Origin
#### Kagi Extension


## Libraries and Other Packages
---
#### `fontconfig-devel`
#### `libX11-dev(el)`
(capitalization of `X` or `x` maybe matters?)
On Raspberry Pi (Debian) it's `libx11-dev` 
#### `libXi-dev(el)`
#### `libXcursor-dev(el)`
#### `libXinerama-dev(el)`
#### `libxRandr-dev(el)`
#### `mesa-libGL-devel` and `mesa-libEGL-devel`
#### `libgles-dev`
On Raspberry Pi we need OpenGLES headers like `<GLES3/gl32.h>`
#### `dbus-devel` or `libdbus-1-dev`
#### `libxkbcommon-devel`
#### `wayland-devel`
#### `labwc`
#### `libgtk-4-dev`
#### `libgtk6svg6`
#### `qt6-svg-plugins`



## Fonts, Icons and Themes
---
- Fonts are managed by `fontconfig` library, configured via `/etc/fonts/font.conf` 
- My config has `/usr/share/fonts` and `/usr/local/share/fonts` (and `~/.fonts` deprecated) configured as font search directories
- Cache directory is `~/.fontconfig` 
- After installing a new font, you should run `fc-cache` to refresh the font cache (pass `-v [folder]` to only scan a specific folder, pass `-f` to force refresh)
- Run `fc-list` to get a printout of available fonts
#### FiraCode Nerd Font
Also **FiraMono Nerd Font**
Copy into `/usr/share/fonts/opentype/fira-code`/`fira-mono`
#### breeze
`breeze` and `breeze-icon-theme` 
#### qt5-gtk-platformtheme
#### oxygen-icon-theme
#### kde-config-gtk-style
