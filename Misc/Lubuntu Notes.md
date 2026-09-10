# Notes
## Desktop
- [ ] Installed January 7th 2026 - 150GB partition on BigSSD
- [ ] Lubuntu 25.10 (Questing Quokka) LXQt 2.2.0
- [ ] History of all shell commands is saved to `~/.bash_history`
- [ ] Installed `ubuntu-restricted-extras` to try and get videos working in the browser ==EDIT:== **Don't do this!** `libopenh264-8` was a problem on my desktop!
- [ ] `xrandr --listmonitors` output:
```
Monitors: 3
 0: +*DP-4 2560/597x1440/336+1920+0  DP-4
 1: +HDMI-0 1920/553x1080/309+4480+360  HDMI-0
 2: +DP-0 1920/544x1080/303+0+360  DP-0
```
 ![[LubuntuMonitorPlacement.png]]
- [ ] Added `xrandr --output DP-4 --mode 2560x1440` it `/usr/share/sddm/scripts/Xsetup` script inside `_mainFn()`
- [ ] VLC has massive text and icons
	- [ ] Added `QT_AUTO_SCREEN_SCALE_FACTOR=0` line to `/etc/environment`
- [ ] Configured `xscreensaver-settings` to use *Decay Screen* mode with slightly higher framerate, shorter duration, and melt away from center style (*Cubic Grid* and *Block Tube* were also potentially good options)
- [ ] Installed `gimp` and `revolt`
- [ ] Window Managers (Tilers) [Reddit](https://www.reddit.com/r/LXQt/comments/1gpc95m/which_window_manager_performs_best_with_lxqt/)
	- [ ] `openbox` Default manager for Lubuntu
	- [ ] `i3-wm` [Website](https://i3wm.org/) **INSTALLED** (it's *butts*)
	- [ ] `sway`
	- [ ] `xfwm4` [Docs](https://docs.xfce.org/xfce/xfwm4/start) **INSTALLED** (doesn't show up in login screen) (primarily for `Xfce4` DE but works as window manager on GNOME and KDE)
	- [ ] `kwin_wayland`
	- [ ] `fluxbox`
	- [ ] `icewm`
	- [ ] `bspwm`: Binary space partitioning window manager [Github](https://github.com/baskerville/bspwm?ref=itsfoss.com) 
- [ ] **Alt+Shift+Left/Right** was being consumed by Openbox to switch windows directionally. I disabled this by commenting out a portion of `~/.config/openbox/rc.xml` and then running `openbox --reconfigure`
- [ ] Jan 9sth 2026 - Installed Spotify
	- [ ] Downloaded `/etc/apt/trusted.gpg.d/spotify.gpg` from `https://download.spotify.com/debian/pubkey_5384CE82BA52C83A.asc`
	- [ ] Added `/etc/apt/sources.list.d/spotify.list` with `deb https://repository.spotify.com stable non-free` inside
	- [ ] Then installed `spotify-client`
- [ ] Picom settings allow you to change opacity of unfocused windows and titlebars. Somehow that got turned on and I had to find it to turn it off again
- [ ] Lubuntu has *Pipewire-Pulse* installed, not *PulseAudio* (so `pacmd` doesn't work)
- [ ] `wpctl status` lists available audio devices. Then `wpctl set-default [number]` to set default `sink` or `source` (or `wpctl set-default-skin [name]` and `wpctl set-default-source [name]`) Also try `pw-cli list-objects Node`
- [ ] Installed `cmake` so I could get Tracy profiler GUI built. Also installed `build-essential` and `libssl-dev`, `libxkbcommon-dev`, `libegl-dev`, `libwayland-dev`
- [ ] Added `cd ~/MyStuff` to the end of `~/.bashrc` in order to change the default working directory of new terminals
- [ ] When creating a launcher on the desktop (Right Click -> Create Launcher) it usually gets placed offscreen by default. To get it back we can select all desktop elements with **Ctrl+A** and drag until we see the new icon, then we move it near the others and move them all back to where they were
- [ ] Installed *Kitty*, *Terminator*, *Tilix*, and *Xfce4 Terminal*. Decided to try using Tilix as default terminal emulator
- [ ] In LXQt Keyboard Shortcut settings I changed the command for **Ctrl+Alt+T** to run `x-terminal-emulator` instead of `qterminal`
- [ ] Removed `gstreamer1.0-plugins-bad` and all it's dependencies (which included `libopenh264-8` which might have been causing Firefox video playback issues). Also removed `ubuntu-restricted-extras` (had to reboot and redo my monitor resolution/layout afterwards, not sure if it's related)
- [ ] Installed `numlockx` to try and get numlock enabled by default after rebooting
- [ ] Installed `vim-gtk3`
- [ ] Fixed dropdown opacity by going into *PiCom* -> *Window Types* -> *Dropdown menu* / *Popup menu* / *Tooltip menu* and setting Opacity to `1.00`
- [ ] Changed the `PS1` in `~/.bashrc` to preferred: [[Bash Terminal Prompt (PS1)]]
- [ ] Change Tilix *Add terminal right* shortcut **Ctrl+Alt+R** to **Ctrl+Backslash**
- [ ] Openbox [Github](https://github.com/danakj/openbox) [Website](https://openbox.org/) 
- [ ] Changed default view mode for file dialog to "Compact View" by changing a line in `~/.config/lxqt/filedialog.conf` -> `Mode=Compact`
- [ ] Manually added favorite items to start menu by adding paths to `.desktop` files under the `[fancymenu]` section in `~/.config/lxqt/panel.conf` (Tracy Profiler, CSwitch, Prism Launcher)
- [ ] Default program for various file types is saved in `~/.config/lxqt-mimeapps.list` or maybe `~/.config/mimeapps.list`?
- [ ] Default placement of new windows can be changed in `~/.config/openbox/rc.xml`. Most things are set to spawn on the monitor where the mouse currently is. So global shortcuts like **Ctrl+Alt+T** will spawn the terminal on whichever monitor the mouse is hovering
- [ ] Enabled smooth resizing by setting `<drawContents>yes</drawContents>` in `~/.config/openbox/rc.xml`. Also changed `<allDesktops>no</allDesktops>` in **Alt+Tab** binding
- [ ] Added **Ctrl+Shift+Escape** binding for `qps` (Task Manager) and **Calc** binding for `qalculate`
- [ ] Installed Steam, tried to get Proton working for Return of the Obra Dinn but failed. Steam has a bunch of weird bugs where it wont respond to selections or open windows
- [ ] Installed "Eye of Gnome" (aka `eog`) as a better default image viewer
- [ ] Fixed font in Konsole by setting it to `Noto Mono` instead of `Noto Sans` (which wasn't installed so it was finding `Noto Sans SignWriting` which is super wierd). You have to create a new profile in order to change *Appearance* options which includes fonts. Also installed a Monokai theme for Konsole
- [ ] Set the default Terminal as Tilix in Plasma so Dolphin (file browser) will open Tilix when right clicking in a folder and selecting "Open in Terminal"
- [ ] Installed *Spectacle* and configure keybindings for PrntScrn, Shift+PrntScrn, and Ctrl+PrntScrn
- [ ] Installed *GHex* for binary file viewing
- [ ] Installed *Waycheck* which displays which extension the running Wayland compositor supports
- [ ] Installed *KeePassXC* from Discover instead of `keepass2` from apt and it works WAY better
- [ ] Installed *Bustle*, a D-Bus message visualizer (Could also try *D-Spy*)
- [ ] Installed *Audacious* a lightweight audio player
- [ ] Installed `meson` to test building Wayfinder from source
- [ ] Installed `qmake6`, `qt6-wayland-dev`, 
- [ ] Installed *VS Code* via `.deb` package
- [ ] Installed `npm` which depends on a **bunch** of packages
## Laptop
- [ ] *Jan 18th 2026* - Installed Tilix, changed `PS1` and cwd in `~/.bashrc`. Fixed window opacity in Picom, and updated widgets in taskbar. Installed `apt-file`. Removed `ubuntu-restricted-extras` and autoremoved dependencies. Changed default terminal to Tilix with `sudo update-alternatives --config x-terminal-emulator` and modifying LXQt keyboard shortcut for **Ctrl+Alt+T**
- [ ] Change Tilix *Add terminal right* shortcut **Ctrl+Alt+R** to **Ctrl+Backslash**
- [ ] ==TODO:== Install Spotify
- [ ] Installed `git-credential-oauth` [Github](https://github.com/hickford/git-credential-oauth?tab=readme-ov-file)
	- [ ] Allows calling `git credential-oauth`
- [ ] Changed [Kvantum](https://github.com/tsujan/Kvantum) theme to `KvArcDark` in *Kvantum Manager*
- [ ] In LXQt Configuration Center:
	- [ ] *Appearance* -> *Widget Style* -> *Qt Style* = `kvantum-dark`
		- [ ] `Breeze` has problems with menu button text being dark on dark (in file explorer)
		- [ ] `Fusion` has problems with tool icons being light on light (in FeatherPad, and Qalculate)
	- [ ] *Appearance* -> *LXQt Theme* = `Lubuntu Arc`
	- [ ] *Appearance* -> *LXQt Theme* -> *GTK 2 Theme* -> `Arc-Dark`
	- [ ] *Appearance* -> *LXQt Theme* -> *GTK 3 Theme* -> `Arc-Dark`
- [ ] In OpenBox Settings:
	- [ ] *Theme* = `Onyx`
- [ ] Installed `cmake` so I could get Tracy profiler GUI built. Also installed `build-essential` and `libssl-dev`, `libxkbcommon-dev`, `libegl-dev`, `libwayland-dev`, `libxrandr-dev`, `libglfw3-dev`
- [ ] Installing `kde-plasma-desktop`. Dependencies:
```
Installing dependencies:
  aha                        kfind                           libfprint-2-2                libkf5iconthemes-data     libkf6holidays-data            libpam-kwallet-common             libxdgutilsbasedir1.0.1                  qml-module-qtgraphicaleffects
  appmenu-gtk-module-common  kgamma                          libfprint-2-tod1             libkf5iconthemes5         libkf6holidays6                libpam-kwallet5                   libxdgutilsdesktopentry1.0.1             qml-module-qtqml-models2
  appmenu-gtk3-module        kglobalacceld                   libfuse2t64                  libkf5itemviews-data      libkf6i18nlocaledata6          libphonon-l10n                    libxkbregistry0                          qml-module-qtquick-controls2
  baloo6                     khelpcenter                     libgit2-1.9                  libkf5itemviews5          libkf6modemmanagerqt6          libphonon4qt6-4t64                libxml2-utils                            qml-module-qtquick-layouts
  bluedevil                  khelpcenter-data                libibus-1.0-5                libkf5jobwidgets-data     libkf6newstuffwidgets6         libplasma-geolocation-interface6  libxmlsec1-openssl1                      qml-module-qtquick-templates2
  breeze                     kinfocenter                     libipt2                      libkf5jobwidgets5         libkf6notifyconfig-data        libplasma5support-data            libzip5                                  qml-module-qtquick-window2
  breeze-wallpaper           kio                             libjs-jquery                 libkf5kiocore5            libkf6notifyconfig6            libplasma5support6                milou                                    qml-module-qtquick2
  bup                        kio-extras                      libjs-underscore             libkf5kiofilewidgets5     libkf6pty-data                 libplasma6                        ocean-sound-theme                        qml6-module-org-kde-activities
  bup-doc                    kio-extras-data                 libkdcrawqt6-5               libkf5kiogui5             libkf6pty6                     libplasmaactivities6              oxygen-sounds                            qml6-module-org-kde-baloo
  catdoc                     kmenuedit                       libkdecorations3-6           libkf5kiontlm5            libkf6pulseaudioqt5            libplasmaactivitiesstats1         par2                                     qml6-module-org-kde-breeze
  clinfo                     konsole                         libkdecorations3private2     libkf5kiowidgets5         libkf6runner6                  libplasmaquick6                   phonon-backend-vlc-common                qml6-module-org-kde-draganddrop
  cryfs                      konsole-kpart                   libkdsoap-qt6-2              libkf5kirigami2-5         libkf6su-bin                   libpolkit-qt5-1-1                 phonon4qt6                               qml6-module-org-kde-graphicaleffects
  docbook-xml                kpackagelauncherqml             libkdsoapwsdiscoveryclient0  libkf5notifications-data  libkf6su-data                  libpowerdevilcore2                phonon4qt6-backend-vlc                   qml6-module-org-kde-guiaddons
  docbook-xsl                kpackagetool5                   libkexiv2qt6-0               libkf5notifications5      libkf6su6                      libprocesscore10                  plasma-activities-bin                    qml6-module-org-kde-kholidays
  dolphin                    kscreen                         libkf5archive-data           libkf5package-data        libkf6svg6                     libpskc0t64                       plasma-browser-integration               qml6-module-org-kde-kirigamiaddons-tableview
  dolphin-data               ksshaskpass                     libkf5archive5               libkf5package5            libkf6syntaxhighlighting-data  libpulsedsp                       plasma-desktop                           qml6-module-org-kde-kquickcontrols
  dolphin-doc                ksystemstats                    libkf5auth-data              libkf5quickaddons5        libkf6syntaxhighlighting6      libqaccessibilityclient-qt6-0     plasma-desktop-data                      qml6-module-org-kde-kquickcontrolsaddons
  dolphin-plugins            kup-backup                      libkf5authcore5              libkf5service-bin         libkf6texteditor-bin           libqcoro6dbus0t64                 plasma-desktoptheme                      qml6-module-org-kde-ksvg
  drkonqi                    kwayland-integration            libkf5bookmarks-data         libkf5service-data        libkf6texteditor-data          libqmobipocket6-3                 plasma-disks                             qml6-module-org-kde-ksysguard
  edid-decode                kwayland5-data                  libkf5bookmarks5             libkf5service5            libkf6texteditor-katepart      libqt5printsupport5t64            plasma-firewall                          qml6-module-org-kde-kwindowsystem
  elfutils                   kwin-common                     libkf5codecs-data            libkf5solid5              libkf6texteditor6              libqt5qmlworkerscript5            plasma-integration                       qml6-module-org-kde-networkmanager
  ffmpegthumbs               kwin-data                       libkf5codecs5                libkf5solid5-data         libkf6texttemplate6            libqt5quickcontrols2-5            plasma-nm                                qml6-module-org-kde-notifications
  fonts-hack                 kwin-style-aurorae              libkf5completion-data        libkf5sonnet5-data        libkf6unitconversion-data      libqt5quicktemplates2-5           plasma-pa                                qml6-module-org-kde-pipewire
  fonts-noto-hinted          kwin-style-breeze               libkf5completion5            libkf5sonnetcore5         libkf6unitconversion6          libqt5texttospeech5               plasma-session-wayland                   qml6-module-org-kde-plasma-plasma5support
  fonts-noto-ui-core         kwin-wayland                    libkf5config-bin             libkf5sonnetui5           libkf6userfeedbackwidgets6     libqt6keychain1                   plasma-systemmonitor                     qml6-module-org-kde-quickcharts
  fonts-noto-unhinted        kwrite                          libkf5config-data            libkf5style5              libkfontinst6                  libqt6positioning6-plugins        plasma-thunderbolt                       qml6-module-org-kde-syntaxhighlighting
  fprintd                    kwrited                         libkf5configcore5            libkf5textwidgets-data    libkfontinstui6                libqt6positioningquick6           plasma-vault                             qml6-module-qtpositioning
  frameworkintegration6      libappimage1.0abi1t64           libkf5configgui5             libkf5textwidgets5        libkglobalacceld0              libqt6sensors6                    plasma-workspace                         qml6-module-qtquick-effects
  gdb                        libappmenu-gtk3-parser0         libkf5configwidgets-data     libkf5wallet-bin          libklipper6                    libqt6serialport6                 plasma-workspace-data                    qml6-module-qtquick-tooling
  gocryptfs                  libasm1t64                      libkf5configwidgets5         libkf5wallet-data         libkmpris6                     libqt6uitools6                    plasma5-integration                      qml6-module-qtquick-virtualkeyboard
  ibus-data                  libbabeltrace1                  libkf5coreaddons-data        libkf5wallet5             libkpipewire-data              libqt6virtualkeyboard6            polkit-kde-agent-1                       qtspeech5-speechd-plugin
  javascript-common          libbaloowidgets-bin             libkf5coreaddons5            libkf5waylandclient5      libkpipewire6                  libqt6webenginewidgets6           power-profiles-daemon                    samba-common
  kactivitymanagerd          libbatterycontrol6              libkf5crash5                 libkf5widgetsaddons-data  libkpipewiredmabuf6            libquickcharts1                   powerdevil                               samba-common-bin
  kate                       libboost-chrono1.83.0t64        libkf5dbusaddons-bin         libkf5widgetsaddons5      libkpipewirerecord6            libquickchartscontrols1           powerdevil-data                          sgml-data
  kate-data                  libboost-filesystem1.83.0       libkf5dbusaddons-data        libkf5windowsystem-data   libkquickcontrolsprivate0      libscim8v5                        pulseaudio-utils                         smartmontools
  kde-baseapps               libboost-filesystem1.88.0       libkf5dbusaddons5            libkf5windowsystem5       libkscreenlocker6              libsdl2-2.0-0                     python3-fuse                             socat
  kde-cli-tools              libboost-program-options1.83.0  libkf5declarative-data       libkf5xmlgui-bin          libksysguard-bin               libsource-highlight-common        python3-ldb                              sonnet-plugins
  kde-cli-tools-data         libboost-thread1.83.0           libkf5declarative5           libkf5xmlgui-data         libksysguard-data              libsource-highlight4t64           python3-pylibacl                         systemsettings
  kde-config-gtk-style       libc6-dbg                       libkf5doctools5              libkf5xmlgui5             libksysguardformatter2         libspdlog1.15                     python3-pyxattr                          tdb-tools
  kde-config-screenlocker    libcanberra-pulse               libkf5globalaccel-bin        libkf6baloo6              libksysguardsensorfaces2       libsquashfuse0                    python3-samba                            vulkan-tools
  kde-config-sddm            libcolorcorrect6                libkf5globalaccel-data       libkf6balooengine6        libksysguardsensors2           libstoken1t64                     python3-sentry-sdk                       wayland-utils
  kde-inotify-survey         libddcutil5                     libkf5globalaccel5           libkf6baloowidgets6       libksysguardsystemstats2       libtaskmanager6                   python3-talloc                           xsettingsd
  kde-style-breeze-qt5       libdisplay-info-bin             libkf5globalaccelprivate5    libkf6calendarevents6     libkwin6                       libtomcrypt1                      python3-tdb                              xwayland
  kde-style-oxygen-qt6       libdisplay-info2                libkf5guiaddons-bin          libkf6declarative-data    libkworkspace6-6               libtommath1                       python3-tornado                          xwaylandvideobridge
  kded5                      libdolphinvcs6                  libkf5guiaddons-data         libkf6dnssd-data          libnotificationmanager1        libtss2-tcti-libtpms0t64          qdbus-qt6
  kdegraphics-thumbnailers   libeditorconfig0                libkf5guiaddons5             libkf6dnssd6              libopenconnect5                libtss2-tcti-spi-helper0t64       qml-module-org-kde-kirigami2
  kdenetwork-filesharing     libeis1                         libkf5i18n-data              libkf6filemetadata-bin    liboxygenstyle6-6              libtss2-tctildr0t64               qml-module-org-kde-kquickcontrolsaddons
  kdoctools6                 libepub0                        libkf5i18n5                  libkf6filemetadata-data   liboxygenstyleconfig6-6        libweather-ion7                   qml-module-org-kde-qqc2desktopstyle
  kf6-breeze-icon-theme      libfmt10                        libkf5iconthemes-bin         libkf6filemetadata3       libpam-fprintd                 libxcb-record0                    qml-module-org-kde-sonnet
```
- [ ] Changed `~/my_stuff` to just `~/my` and routed most of my user directories to folders inside that (by changing `~/.config/user-dirs.dirs`). Updated all the custom `.desktop` files I made in `/usr/share/applications`
- [ ] Customized Dolphin and installed "Open in Tilix" context menu option. For some reason I couldn't add Tilix option to topbar as a button, only the old "Open in Terminal" which opens Konsole
- [ ] Dolphin Bookmarks:
![[DolphinBookmarksLaptop.png]]
- [ ] Added the following line the `/etc/fstab`:
	`UUID=C492096E920965F0 /mnt/DiskD ntfs-3g defaults,nls=utf8,umask=000,dmask=000,fmask=000,uid=1000,gid=1000,windows_names 0 0`
- [ ] Installed *Spectacle* for taking screenshots (since *ScreenGrab* seems to not work in KDE Plasma). Configured save location and file name and made it save and copy to clipboard after screenshot
- [ ] Changed launch menu icon in taskbar: ![[rocket_icon64.png]]
- [ ] Installed `npm` which depends on a **bunch** of packages (include `nodejs`)
	- Npm **v9.2.0**, Node **v20.19.4**
- [ ] 

## Global Shortcuts
- [ ] **Ctrl+Alt+Arrow**: Switch desktops
- [ ] **Ctrl+Alt+Shift+Arrow**: Move focused window between desktops
- [ ] **Alt+Space**: Bring up menu for current window (to move, resize, change layer, etc.)
- [ ] **Alt+Escape**: Send current window to back of focus
- [ ] **Alt+Tab**: Switch focus between windows
- [ ] **F11**: Toggle fullscreen
- [ ] **Alt+LeftClick**: Move Window
- [ ] **Alt+RightClick**: Resize window
- [ ] **Alt+MiddleClick**: Send window to back of focus
- [ ] **DoubleCick** (On titlebar): Toggle window maximized
- [ ] **MiddleClick** (On Maximize button): Toggle resize max window to screen height
- [ ] **RightClick** (On Maximize button): Toggle resize max window to screen width
## QTerminal Shortcuts
- [ ] **Ctrl+Shift+M**: Toggle top menu bar

---
# Installation
- [ ] **Date:** January 7th 2026
- [ ] **Distro:** Lubuntu 25.10 (Questing Quokka) LXQt 2.2.0 Desktop 64-bit - Downloaded January 4th 2026 - [Download](https://lubuntu.me/downloads/) - `lubuntu-25.10-desktop-amd64.iso`
- [ ] **Hard Drive:**
	- [ ] **Name:** Samsung SSD 870 EVO 2TB *or* `sdd`
	- [ ] **Windows Name:** F: - BigSSD - Disk 2
	- [ ] **Capacity:**
		- [ ] **Total Capacity:** `1.82 TB` (or `1,863 GB` or `1,907,713 MB` or about `2,000,381,014,016 bytes`)
		- [ ] **NTFS Partition:** `1.67 TB` (or `1,713 GB` or `1,754,112 MB` or `1,839,319,740,416 bytes`)-
		- [ ] **Unallocated Partition:** `150 GB` (or `153,600 MB` or `157,286,400 KB` or `161,061,273,600 bytes`)
	- [ ] **Location Info:** Bus Number 2, Target Id 0, LUN 0, `\_SB.PCI0.SAT0.PRT2`
	- [ ] **Install Date:** 11/5/2023 7:40:02 PM
	- [ ] **Partition syle:** GUID Partition Table (GPT)
- [ ] **Bootable USB Drive:** RedUSB (E:) VendorCo ProductCode (64GB)
- [ ] **Bootable USB Making Software:** Ventoy (`F:/Programs/ventoy/Ventoy2Disk.exe`) with 1.1.05 exFAT MBR
- [ ] **CPU:** Intel Core i7-6700K @ 4.00GHz (8 CPUs)
- [ ] **Graphics Card:** NVIDIA GeForce RTX 3060 Ti
- [ ] **Windows GPU Driver:** Version=32.0.15.7628 Date=04/26/2025 Model=WDDM 2.7
- [ ] [GPU Driver Installation Instructions](https://linuxvox.com/blog/ubuntu-and-nvidia-drivers/)
	- [ ] `sudo apt update && sudo apt upgrade`
	- [ ] `lspci | grep -i nvidia`
	- [ ] `sudo add-apt-repository ppa:graphics-drivers/ppa`
	- [ ] `sudo apt update`
	- [ ] `sudo apt install nvidia-driver-<version>`
	- **or**
	- [ ] Download from NVidia Website
	- [ ] `cd` to the downloaded folder
	- [ ] `chmod +x NVIDIA-Linux-x86_64-<version>.run`
	- [ ] Stop the X Server to avoid conflicts during installation (**Ctrl+Alt+F3** then login)
	- [ ] `sudo systemctl stop lightdm`
	- [ ] `sudo ./NVIDIA-Linux-x86_64-<version>.run`
	- [ ] Follow on-screen instructions
- [ ] [Linux Hard Drive Naming Scheme](https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme)
	- [ ] `fd`=SATA (aka floppy), `sd`=SCSI/SATA, `hd`=IDE
	- [ ] Third letter is device order, `a`, `b`, `c`, etc.
	- [ ] Number is partition index (starting at `0`)
- [ ] [Windows Disk Management Screenshot](Private/Images/WindowsDiskParition_screenshot_01_07_2026.png)
- [ ] All Hard Drives
	- [ ] `(C:)` - `sdc` - **Local Disk** - SanDisk Ultra II 480GB
		- [ ] Bus 1 - Disk 1
		- [ ] `457,863 MB`/`457,203 MB` (3MB unallocated, 128MB reserved)
		- [ ] Partitions: 446.49GB (Windows) - 529MB (Recovery)
		- [ ] GUID Partition Table (GPT)
	- [ ] `(D:)` - `sdb` - **Local Disk** - WDC WD10EZEX-00WN4A0
		- [ ] Bus 0 - Disk 0
		- [ ] `953,870 MB`/`703,302 MB` (2MB unallocated, 16MB reserved)
		- [ ] Partitions: 450MB (Recovery) - 100MB (EFI) - 686.82GB (Windows) - 228.22GB (Ubuntu) - 15.92GB (Swap?)
		- [ ] GUID Partition Table (GPT)
		- [ ] Has Grub installed but doesn't seem to be working properly? Shows as `Ubuntu (SATA6G_1: WDC WD10EZEX-00WN4A0)`
	- [ ] `(F:)` - `sdd` - **BigSSD** - Samsung SSD 870 EVO 2TB 
		- [ ] Bus 2 - Disk 2
		- [ ] `1,907,713 MB`/`1,754,112 MB` (153601MB unallocated, 0MB reserved)
		- [ ] GUID Partition Table (GPT)
	- [ ] `(G:)` - `sda` - **Block** - Seagate Expansion SCSI Disk Device
		- [ ] Bus 0 - Disk 4
		- [ ] `953,869 MB`/`953,867 MB` (2MB unallocated, 0MB reserved)
		- [ ] Master Boot Record (MBR)
	- [ ] `(Q:)` - `sde` - **QuestLog** - HGST HUS724040ALA640
		- [ ] Bus 4 - Disk 3
		- [ ] `3,815,448 MB`/`3,815,430 MB` (2MB unallocated, 16MB reserved)
		- [ ] GUID Partition Table (GPT)
	- [ ] `(?:)` - `sdf` - **Ventoy** - VendorCo ProductCode
- [ ] [How to boot linux from grub](https://askubuntu.com/questions/929833/how-do-i-boot-my-pc-from-grub) ([Screenshot](grub_instructions_from_stackoverflow.png))
- [ ] Probably want to boot `(hd1,gpt5)` or `sdb5` cause it's `ext` format and `239,310,848 KB` and has `vmlinuz` and `initrd.img` in the root
- [ ] 