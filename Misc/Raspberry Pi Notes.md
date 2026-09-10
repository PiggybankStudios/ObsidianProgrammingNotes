Also see [[Linux Notes]]
# Notes
- [ ] User Guide is stored at `/usr/share/userguide/The_Official_Raspberry_Pi_Beginners_Guide_6th_Edition.pdf` [File Link](file:///usr/share/userguide) 
- [ ] [Pi 500 Keyboard Computer](https://www.amazon.com/Compatible-Raspberry-Quad-Core-Processor-Bluetooth/dp/B0DSC5XD6D) 
- [ ] Hold down **Space** while the Pi boots to enter the bootloader? (explained in network flow for Raspberry Pi Imager, when you start with a blank SD card)
- [ ] TTYs stands for "Teletypes"
- [ ] **8GB** RAM runs at **4267MHz** (shared between CPU and GPU)
- [ ] Micro-SD card slot supports up to **512GB**
- [ ] WiFi supports **2.4GHz** and **5GHz** 802.11ac networks
- [ ] High-speed PCIe connector could be used for an M.2 SSD
- [ ] Pi-hole [Github](rpimag.co/pi-hole-github) 
	- Install **Raspberry Pi OS Lite (64-bit)** 
	- Connect to Raspberry Pi over SSH `ssh <username>@<device-hostname>.local`
	- `curl -sSL https://install.pi-hole.net | bash`
	- ... See Raspberry Pi Magazine Issue 168, Page 46 for the rest (**Start**->**Help**->**Bookshelf**)
- [ ] ==TODO:== How do we disable the Keystore popup when we open Chrome or Obsidian?
- [ ] Raspberry Pi advanced config can be reached through `sudo raspi-config`
- [ ] Bought a **256GB** SD Card from Target for *$113* on **Aug 6th 2026**. Failed first flash with Raspberry Pi Imager
- [ ] `lsb_release --description` returns `Debian GNU/Linux 13 (trixie)`
- [ ] Installed [Lakka](https://www.lakka.tv/) on the 64GB SD Card for RetroArch-based emulation. Copied a couple of N64 games to flash drive and tested N64 emulation
- [ ] 

# Hotkeys
- [ ] **Ctrl+Alt+T**: Launch Terminal
- [ ] **Ctrl+Alt+Up/Down**: Maximize/Unmaximize window (Also **Win+A** for Unmaximize)
- [ ] **Win+Up/Left/Right/Down**: Move window to top/left/right/bottom half of screen
- [ ] **Ctrl+Alt+F1/F2/.../F6**: Switch to TTY(n) terminal
- [ ] **Ctrl+Alt+F7**: Switch back to graphical mode? ==TODO:== This is recommend as a way to return from **Ctrl+Alt+F2** but maybe the TTY7 is actually supposed to be the default TTY used by the boot process?
- [ ] **Ctrl+Shift+C**/**Ctrl+Shift+V**: Copy/Paste in the terminal
- [ ] **Win+Shift+S**: Screenshot (customized, is also bound to **PrintScrn**)
- [ ] **Alt+Up**: In Dolphin it goes to Parent Folder
- [ ] 

# Installation/Setup - August 2nd 2026
- [ ] Bought a **Raspberry Pi 5 Model B Rev 1.1** 8GB kit from "Vemico" that comes with a case, active cooler,  64GB micro-SD card, etc. It cost *$239.99* for the kit (raspberry pi 4 on it's own would be ~$100) - August 1st 2026 - It has a **ARM Cortex-A76 (4) 2.4GHz** processor
![[RaspberryPi5BoardPicture.jpg]]
- [ ] Download Raspberry Pi Imager and used 64-bit Raspberry Pi image which installed **Debian GNU/Linux 13.5** 
- [ ] Desktop Environment is **Wayland** (**labwc:wlroots**)? Window Manager is **labwc** 
- [ ] Username: `robbitay` Device Name: `RaspPi5` Wifi SSID: `TheBudHole_5GHz` 
- [ ] Terminal is **x-terminal-emulator**?
- [ ] Installed **Sublime Text** and **Sublime Merge** by doing their default instructions:
	- `wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo tee /etc/apt/keyrings/sublimehq-pub.asc > /dev/null`
	- `echo -e 'Types: deb\nURIs: https://download.sublimetext.com/\nSuites: apt/stable/\nSigned-By: /etc/apt/keyrings/sublimehq-pub.asc' | sudo tee /etc/apt/sources.list.d/sublime-text.sources`
	- `sudo apt-get update`
	- `sudo apt-get install sublime-text` and `sudo apt-get install sublime-merge`
- [ ] **Git** was already installed by default, version **2.47.3** 
- [ ] Already installed: **nano**, **make**, **cmake**, **gcc** 
- [ ] Installed via package manager: `clang`, `libdbus-1-dev`, `keepassxc`
- [ ] Downloaded **Obsidian 1.13.4** AppImage Arm64, made it executable with `chmod +x Obisidian-1.13.4.AppImage` and then ran it
- [ ] Installed **lsd** via `sudo apt-get install lsd`
- [ ] Downloaded **FiraCode Nerd Font** and **FiraMono Nerd Font** from [NerdFonts Website](https://www.nerdfonts.com/font-downloads) 
	- [ ] Fonts are managed by `fontconfig` library, configured via `/etc/fonts/font.conf` 
	- [ ] My config has `/usr/share/fonts` and `/usr/local/share/fonts` (and `~/.fonts` deprecated) configured as font search directories
	- [ ] Cache directory is `~/.fontconfig` 
	- [ ] After installing a new font, you should run `fc-cache` to refresh the font cache (pass `-v [folder]` to only scan a specific folder, pass `-f` to force refresh)
	- [ ] Run `fc-list` to get a printout of available fonts
	- [ ] Copied FiraCode and FiraMono into `/usr/share/fonts/opentype/fira-code`/`fira-mono`
- [ ] Downloaded Kurzgesagt wallpapers from [Google Drive](https://drive.google.com/drive/folders/1a4Hbz7Bn-ubmITJkqrwNTWW8zQNr1mwZ) linked by [Reddit Post](https://www.reddit.com/r/kurzgesagt/comments/15pvf7h/kurzgesagt_4k_wallpapers_3840x2160/) 
- [ ] File Manager keeps crashing on second time I drag to extract files from the .zip GUI
- [ ] Installed **tree** via `sudo apt-get install tree`
- [ ] Changed Terminal to use FiraMono and Solarized Dark theme
- [ ] Installed **neofetch** via `sudo apt-get install neowofetch`
```sh
        _,met$$$$$gg.             robbitay@RaspPi5 
     ,g$$$$$$$$$$$$$$$P.          ---------------- 
   ,g$$P"        """Y$$.".        OS: Debian GNU/Linux 13.5 (trixie) aarch64 
  ,$$P'              `$$$.        Host: Raspberry Pi 5 Model B Rev 1.1 
 ',$$P       ,ggs.     `$$b:      Kernel: 6.18.34+rpt-rpi-2712 
 `d$$'     ,$P"'   .    $$$       Uptime: 1 hour, 35 mins 
  $$P      d$'     ,    $$P       Packages: 293 (pip), 1695 (dpkg) 
  $$:      $$.   -    ,d$$'       Shell: bash 5.2.37 
  $$;      Y$b._   _,d$P'         Resolution: 1920x1080 
  Y$$.    `.`"Y$$$$P"'            DE: labwc:wlroots (wayland) 
  `$$b      "-.__                 WM: labwc 
   `Y$$                           Theme: PiXonyx [GTK3] 
    `Y$$.                         Icons: PiXtrix [Qt/GTK3] 
      `$$b.                       Cursor: PiXtrix [Qt/GTK3] 
        `Y$$b.                    Terminal: x-terminal-emulator 
           `"Y$b._                CPU: ARM Cortex-A76 (4) @ 2.40 GHz 
               `"""               Memory: 2.59 GiB / 7.86 GiB (32%) 
                                  Network: Wifi6 
```
- [ ] Installing **Discord** (following [pimylifeup](https://pimylifeup.com/raspberry-pi-discord/))
	- [ ] Install **curl** `sudo apt-get install curl`
	- [ ] `curl -fsSL https://apt.armcord.app/public.gpg | sudo gpg --dearmor -o /usr/share/keyrings/armcord.gpg` 
	- [ ] Could not resolve host: apt.armcord.app
	- [ ] ArmCord (and WebCord) are third-party clients
	- [ ] Logged into Web version instead
- [ ] Downloaded **Fred**
	- [ ] No ARM64 Linux version yet.
	- [ ] Discord people say maybe I could use [FEX](https://fex-emu.com/) [Github](https://github.com/FEX-Emu/FEX) or [Box64](https://box86.org/) [Github](https://github.com/ptitSeb/box64) paired with Wine?
	- [ ] Downloading [FEX-2607](https://github.com/FEX-Emu/FEX/releases/tag/FEX-2607) release
	- [ ] [Wiki - Setting up FEX](https://wiki.fex-emu.com/index.php/Development:Setting_up_FEX) 
	- [ ] README.md from the release says I could install through a "PPA" by doing `curl --silent https://raw.githubusercontent.com/FEX-Emu/FEX/main/Scripts/InstallFEX.py | python3`
		- [ ] Results in "debian 13" is not a supported distro
- [ ] Installing OAuth support for git:
	- [ ] `sudo apt-get install git-credential-oauth`
	- [ ] `git credential-oauth configure`
- [ ] Installed **micro** via `sudo apt-get install micro`
- [ ] Copied [[Git Config]] into `~/.gitconfig` so we can have aliases like `git s`, `git a`, etc.
- [ ] Getting a black screen with mouse now after restarting
	- [ ] Somebody says **Ctrl+Alt+F1** to get to terminal and then do `sudo service lightdm restart` 
	- [ ] Maybe something to do with `/boot/firmware/cmdline.txt`?
	- [ ] `service --status-all`
	- [ ] Ran `sudo apt install labwc` and then `sudo reboot` 
	- [ ] `lightdm --show-config`
	- [ ] Running `labwc-pi` in the **Ctrl+Alt+F2** terminal *worked*!
	- [ ] LightDM configuration is at `/etc/lightdm/lightdm.conf`
	- [ ] LightDM log is located at `/var/log/lightdm/lightdm.log` 
	- [ ] Tried `sudo raspi-config nonint do_boot_behaviour B4`
	- [ ] Logs have lines like `Failed to write utmpx: No such file or directory`
	- [ ] May be related to **Debian bug #1094353**?
	- [ ] 
- [ ] Running `sudo apt-get upgrade` (Accidentally rebooted in the middle!)
```
The following packages will be upgraded:
  base-files chromium chromium-common chromium-l10n chromium-sandbox cups cups-client cups-common cups-core-drivers
  cups-daemon cups-ipp-utils cups-ppdc cups-server-common dhcpcd-base dirmngr ffmpeg firefox firmware-atheros
  firmware-brcm80211 firmware-libertas firmware-mediatek firmware-realtek gnupg-utils gpg gpg-agent gpg-wks-client
  gpgconf gpgsm gpgv gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-good hplip hplip-data libass9
  libavcodec61 libavdevice61 libavfilter10 libavformat61 libavutil59 libcups2t64 libcupsimage2t64 libdtovl0
  libexpat1 libexpat1-dev libgd3 libgif7 libgpiolib0 libgraphite2-3 libgstreamer-plugins-bad1.0-0 libhpmud0
  libinput-bin libinput-tools libinput10 libixml11t64 libldb2 liblzma5 libnss3 libntfs-3g89t64 libpisp-common
  libpisp1 libpoppler-cpp2 libpoppler-glib8t64 libpoppler147 libpostproc58 libprotobuf-lite32t64 libprotobuf32t64
  libpython3.13 libpython3.13-dev libpython3.13-minimal libpython3.13-stdlib librpieepromab0 librpifwcrypto0
  libsane-hpaio libsmbclient0 libssh-4 libssh2-1t64 libswresample5 libswscale8 libtalloc2 libtasn1-6 libtdb1
  libtevent0t64 libtiff6 libupnp17t64 libvncclient1 libwbclient0 libwlroots-0.19 libxfont2 libxpm4 linux-libc-dev
  lpplug-volumepulse ntfs-3g pishutdown poppler-utils printer-driver-hpcups printer-driver-postscript-hp
  python3-idna python3-pil python3-urllib3 python3.13 python3.13-dev python3.13-minimal python3.13-tk
  python3.13-venv raindrop raspi-config raspi-config-core raspi-utils raspi-utils-core raspi-utils-dt
  raspi-utils-eeprom raspi-utils-otp raspinfo rasputin rc-gui rpcc rpi-connect rpi-eeprom rpi-imager rpi-loop-utils
  rpi-swap rpieepromab rpifwcrypto rsync samba-libs wfplug-volumepulse wireless-regdb xz-utils
```
- [ ] Start menu files live in `/usr/share/applications` and `/usr/share/raspi-ui-overrides/applications/*.desktop`. Also maybe could put things in `~/.local/share/applications/`?
- [ ] Many tutorials recommend running `sudo apt full-upgrade` after first booting Raspberry Pi (this didn't help the login problem)
- [ ] Cycled the **Control Centre**->**System**->**Boot:** option between *To desktop* and *To cli*. Also turned *Desktop auto login* off. Still didn't fix the login problem
- [ ] Copied KeePass database over using USB. Entered Sublime Text and Sublime Merge licenses. Set Sublime Merge to dark mode and commit message at bottom
- [ ] Changed `~/.config/user-dirs.dirs` 
- [ ] Installed **Dolphin** via `sudo apt-get install dolphin`.
	- [ ] Then installed `breeze-icon-theme` to try to get the icons working.
	- [ ] Couldn't find `kde-runtime` like [one site](https://www.developnsolve.com/linux/how-to-install-dolphin-on-linux) suggested
	- [ ] Created `~/.config/kdeglobals` with:
	```config
	[Icons]
	Theme=breeze-dark
	[General]
	ColorScheme=BreezeDark
	```
	- [ ] Checked breeze icons are installed `lsd /usr/share/icons/breeze`
	- [ ] Updated icon cache `gtk-update-icon-cache /usr/share/icons/breeze`
	- [ ] `sudo apt-get install oxygen-icon-theme kde-config-gtk-style`
	- [ ] Tried `export QT_QPA_PLATFORMTHEME=gtk3`
	- [ ] Made sure `libqt5svg5` was installed
	- [ ] `sudo apt-get install qt5-gtk-platformtheme`
	- [ ] Verify icons are installed with `dpkg -L breeze-icon-theme`
	- [ ] Noticed errors when running dolphin from the terminal
	- [ ] Also tried `QT_DEBUG_PLUGINS=1 dolphin`
	- [ ] **Seems like current RaspberryPi OS ships with Qt6 *not* Qt5**
	- [ ] *Solution:* `sudo apt-get install qt6-svg-plugins` (`libqt6svg6` used to ship the plugin, but now it only ships the `.so` and the plugin has to be installed separately)
- [ ] Installed **Claude Desktop** app by following [Linux instructions](https://code.claude.com/docs/en/desktop-linux) 
	- [ ] `sudo apt install curl gnupg`
	- [ ] `sudo curl -fsSLo /usr/share/keyrings/claude-desktop-archive-keyring.asc https://downloads.claude.ai/claude-desktop/key.asc`
	- [ ] `gpg --show-keys /usr/share/keyrings/claude-desktop-archive-keyring.asc`
	- [ ] `echo "deb [arch=arm64 signed-by=/usr/share/keyrings/claude-desktop-archive-keyring.asc] https://downloads.claude.ai/claude-desktop/apt/stable stable main" | sudo tee /etc/apt/sources.list.d/claude-desktop.list`
	- [ ] `sudo apt update` and `sudo apt install claude-desktop`
- [ ] Configured *Time Format* for the click widget to `%I:%M %p`
- [ ] For multiple desktops I tried installing `obconf`  (OpenBox configurator) but it segfaults on startup
- [ ] Switched Launcher to **Firefox**, let it be the default browser, changed the theme to dark
- [ ] Logged into **Kagi** and installed Firefox extension which makes it my default search engine
- [ ] Set **Dolphin** to be default file manager with `xdg-mime default org.kde.dolphin.desktop inode/directory`
- [ ] Installed **Tilix** via `sudo apt-get install tilix`
	- [ ] Changed to *FiraMono Nerd Font Regular* and *Monokai Dark* theme
	- [ ] After first command it popped up a dialog about a VTE-related config issue https://gnunn1.github.io/tilix-web/manual/vteconfig/
	- [ ] Update default terminal with `sudo update-alternatives --config x-terminal-emulator` (could need to add it manually with `sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/<your-term> 50`) (Some apps may read `xdg-mime default <your-term>.desktop x-scheme-handler/terminal`)
- [ ] Global keybindings live in `/etc/xdg/labwc/rc.xml`. We also have `~/.config/labwc/rc.xml`. Added to the .config folder one, then rebooted:
```xml
  <keyboard>
  	<keybind key="C-A-t">
      <action name="Execute">
         <command>tilix</command>
      </action>
    </keybind>
  </keyboard>
```
- [ ] Unbound the global hotkey **Ctrl+Alt+W** which opened the WiFi panel by adding the following and then running `labwc --reconfigure` (used to run `wfpanelctl netman menu`)
```xml
<keybind key="C-A-w" />
```
- [ ] **Ctrl+Alt+Space** was also bound to `gui-pkinst orca reboot` which installs a screen reader and then reboots
- [ ] Added **Win+Shift+S** as screenshot hotkey by adding
```xml
<keybind key="W-S-s"><action name="Execute"><command>grim</command></action></keybind>
```
- [ ] Set `GRIM_DEFAULT_DIR` to `/home/robbitay/my/images/screenshots` by editing `/etc/environment`
- [ ] Fixed "Open Terminal Here" options in Dolphin by editing `~/.config/kdeglobals`:
```
[General]
TerminalApplication=tilix
TerminalService=com.gexperts.Tilix.desktop
```
- [ ] Installing `breeze` via `sudo apt-get install breeze` 
- [ ] You can also set KDE config values via `kwriteconfig6 --group Icons --key Theme breeze` (also use `kreadconfig6` to read current values)
- [ ] Ran `sudo raspi-config nonint do_boot_behaviour B4` to hopefully fix the auto-login and bypass the greeter that doesn't render
- [ ] The Keyring popup can be permanently disabled if you leave the password fields empty and continue, the secrets will be stored unencrypted on disk. Alternatively we could launch Electron apps with `--password-store=basic` (also accepts `gnome-libsecret`, `kwallet`, `kwallet5`, `kwallet6`). See `libpam-gnome-keyring` and `gnome-keyring-daemon`
- [ ] Made an Obsidian.desktop (Extracted the icon.png out of the AppImage which is just an archive):
```desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=Obsidian
GenericName=Markdown Notes
Comment=An editor for Markdown notes
Exec=/home/robbitay/my/programs/obsidian/Obsidian.AppImage
Terminal=false
MimeType=text/plain;
Icon=/home/robbitay/my/programs/obsidian/icon.png
Categories=Utility;TextEditor;
StartupNotify=true
```
- [ ] Start menu categories are defined by .menu file at `/etc/xdg/menus/` which references .directory files at `/usr/share/desktop-directories/` for how they display (name and icon) (Start menu is `smenu` plugin from `wf-panel-pi`). Category can be: `AudioVideo`, `Audio`, `Video`, `Development`, `Education`, `Game`, `Graphics`, `Network`, `Office`, `Science`, `Settings`, `System`, `Utility`
- [ ] Firefox OAuth workflow for Sublime Merge is hanging. Probably related to Secret Service D-Bus hanging
	- [ ] `sudo apt install libsecret-tools`
	- [ ] `secret-tool store --label=test test foo`
	- [ ] `pgrep -a gnome-keyring` (really looking for `gnome-keyring-daemon` but can't search for things with a pattern longer than 15 characters)
	- [ ] Secret Service seems to be running fine
	- [ ] **Logging out manually and logging back in fixes it**
	- [ ] Keyrings are located in `~/.local/share/keyrings/`
	- [ ] Autostart for gnome secrets exists at `/etc/xdg/autostart/gnome-keyring-secrets.desktop`
	- [ ] Installed **Seahorse** via `sudo apt-get install seahorse`. A GUI for managing secrets and keyrings
	- [ ] Gave up and changed `git config --global credential.helper store` (or really just used `micro` to edit `~/.gitconfig`)
- [ ] Installed `sudo apt-get install libgtk-4-dev` to test `pkg-config gtk4 --cflags`
- [ ] Installed **GIMP** via `sudo apt-get install gimp`

# Installation/Setup of Second SD Card August 6th 2026
- [ ] SD Card is **256GB**, failed to write once in Raspberry Pi Imager and then succeeded
- [ ] Changed to Firefox, installed Kagi Extension
- [ ] Copied Obsidian.AppImage from USB and installed the .desktop file into `~/.local/share/applications`
- [ ] Installed `tilix git keepassxc lsd gimp micro clang kdiff3 make cmake`
- [ ] Set keyring password to same as login. On second popup I checked "auto unlock at login"
- [ ] Installed **Sublime Text** and **Sublime Merge**. Entered licensed, copied settings from SublimeData repo, copied Preferences into Packages/User, installed plugins
- [ ] Set Sublime Text as default for many code-related file types
- [ ] Git clones SublimeData, PigCore, PigBuild, CSwitch, Crest, and COSM
- [ ] Installed Dolphin
	- [ ] `sudo apt install dolphin qt6-svg-plugins`
	- [ ] `xdg-mime default org.kde.dolphin.desktop inode/directory`
	- [ ] Show Hidden Files
	- [ ] In Preferences: *Interface*->*Folders & Tabs*->*Show filter bar*, *Interface*->*Status & Location bars*->*Show full path inside location bar*
	- [ ] `sudo apt install breeze`
	- [ ] `sudo apt install qt6ct`, `micro /etc/environment` set `QT_QPA_PLATFORMTHEME=qt6ct`, relogin, run `qt6ct` (doesn't change Dolphin)
	- [ ] Added `[General]\nColorScheme=BreezeDark` to `~/.config/kdeglobals`
	- [ ] `strace -fe trace=openat dolphin 2>&1 | grep kdeglobals`
	- [ ] `kreadconfig6 --file kdeglobals --group General --key ColorScheme`
	- [ ] I give up on Dark Mode
	- [ ] Added lines to `~/.config/kdeglobals` under `[General]`: `TerminalApplication=tilix` and `TerminalService=com.gexperts.Tilix.desktop`
	- [ ] Configured Toolbar in to include "Up" and "Open Terminal Here", configured terminal button to not show text
- [ ] Added hotkeys to `~/.config/labwc/rc.xml` and ran `labwc --reconfigure`
- [ ] Set `GRIM_DEFAULT_DIR=/home/robbitay/my/images/screenshots` in `/etc/environment`
- [ ] Configured `~/.config/user-dirs.dirs` and deleted `~/Downloads`, `~/Videos`, and `~/Music`
- [ ] Downloaded **FiraCode** and **FiraMono** nerd fonts. Unzipped and then: `sudo cp -r fira-code /usr/share/fonts/opentype/fira-code` and `sudo cp -r fira-mono /usr/share/fonts/opentype/fira-mono`. Changed **Tilix** to **FiraMono** (had to restart Tilix)
- [ ] Following [Raspberry Pi Forum - Setting up Samba File Sharing / NAS](https://forums.raspberrypi.com/viewtopic.php?t=205379)
	- [ ] `sudo apt install samba samba-common-bin smbclient cifs-utils`
	- [ ] `cifs-utils` is Common Internet File System Utilities
	- [ ] Added to the end of `/etc/samba/smb.conf`:
	```conf
	[RaspPi Shared]
	comment = Pi Server
	public = yes
	writeable = yes
	browsable = yes
	path = /home/robbitay/my/shared
	```
	- [ ] Also set `create mask = 0777` and `directory mask = 0777`
- [ ] 