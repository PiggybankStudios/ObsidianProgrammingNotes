- [ ] Ordered a [Raphnet dual N64 controller USB adapter](https://www.lakka.tv/) from **Rythm Gamer** for *$62.96* [Image](RaphnetDualN64ControllerToUsbAdapter.png) 
- [ ] Also ordered a [Hyperkin adapter from Amazon](https://a.co/d/0hlmjTSx) [Image](HyperkinAdapterN64ControllerProductImage.png)
- [ ] Can build a [4dapter](https://github.com/timville85/4dapter) myself? [Image](4dapterImageN64AdapterSelfBuilt.png) 
- [ ] [N64Brew Discord](https://discord.gg/8VNMKhxqQn) 
- [ ] [Analogue 3D](https://www.analogue.co/3d) 
- [ ] [ROM patching online tool](https://www.romhacking.net/patch/) 
- [ ] [UNFLoader](https://github.com/buu342/N64-UNFLoader) - A cross-platform and universal Nintendo64 flashcart ROM uploader, featuring a USB+debug library for libultra and libdragon.
	- [ ] libdragon README also mentions [g64drive](https://github.com/rasky/g64drive) and [ed64](https://github.com/anacierdem/ed64) 
- [ ] [Build Games with Original N64 SDK](https://n64squid.com/homebrew/n64-sdk/) 
- [ ] https://n64brew.dev/wiki/Main_Page
- [ ] 

# Nintendo 64 Hardware
## Images
![[Nintendo64ConsoleAndController.png]]
![[Nintendo64MotherboardLabeled.png]]
![[Nintendo64BlockDiagram.png]]
![[Nintendo64ExpansionPak.png]]
## Notes
- [ ] [Nintendo 64 Architecture](https://www.copetti.org/writings/consoles/nintendo-64/) 
- [ ] Released in **1996**
- [ ] Shipped with **NEC VR4300**: a single core **93.75 MHz** CPU and **Reality Co-Processor (RCP)** running at **62.5 MHz**. **24kB** of L1 Cache (16kB instructions, 8kB data)
- [ ] **4.5MB** of RAM (later expanded to **8MB** with the Expansion Pak). 9-bit address, top bit is reserved for GPU, so other processors only see 4MB
- [ ] Game cartridges were at most **64MB** 
- [ ] Floating Point Unit is designated as Co-Processor (but isn't really?) called CP1
- [ ] RAM follows Unified Memory Architecture (UMA). Graphics chip arbitrates access to RAM. **Rambus DRAM** (RDRAM) is a fast serial architecture for RAM (N64 had "Base DRAM" variant). Delay between memory request and value in cache is around **640ns**. The RAM is clocked at **250MHz** though, so large consecutive writes can be **500MB/s**. NEC’s uPD488170L memory banks
- [ ] The VR4300 includes another coprocessor known as the **System Control Coprocessor** (CP0), which is composed of a **Memory Management Unit** (MMU) and a **Translation Lookaside Buffer** (TLB). The MMU governs how memory is organised and cached. The TLB allows devlopers to define custom memory maps in some mirrors of the physical memory in virtual address space. These mirrors are called **segments**, and each one is connected to distinct circuitry (L1 cache, physical RAM, or TLB-mapped regions). Some segments were designed to distinguish between ‘kernel’ and ‘user’ locations for security purposes. Nevertheless, the N64 always operates in ‘kernel’ mode, making the ‘non-TLB kernel cached’ segment (called ‘KSEG0’) the most commonly used for games.
- [ ] 

# M64 Hardware
## Images
![[M64MotherboardImage.png]]
## Notes
- [ ] 

# Summer Cart 64 ([Website](https://summercart64.dev/) )
## Images
![[SummerCart64PCB_Front.png]]![[SummerCart64PCB_Back.png]]
## Notes
- [ ] [YouTube - How to build and program the SummerCart64](https://www.youtube.com/watch?v=t6hyCFpwqz8) 
- [ ] [sc64-deployer Release v2.20.2](https://github.com/Polprzewodnikowy/SummerCart64/releases/tag/v2.20.2) CLI tool for interacting with the cart over USB
- [ ] [Tutorial - Using SummerCart64](https://64dd.org/tutorial_sc64.html) 
	- [ ] `sc64deployer list` `sc64deployer info` `sc64deployer test`
	- [ ] `sc64deployer set rtc`
	- [ ] `sc64deployer upload [rom.n64] --save-type eeprom4k --save [save.sav]` (`--direct`)
	- [ ] `sc64deployer download [save.sav]`
	- [ ] `sc64deployer de
- [ ] [N64 Flashcart Menu - Docs](https://menu.summercart64.dev/docs/10_getting_started_sd.html) 
- [ ] The cart must have called `joypad_init()` and be calling `joypad_poll()` during it's update loop in order for it to support  the M64 **Z+Start** menu
- [ ] `debugf()` writes to `stderr` and gets compiled out if `NDEBUG` is defined. Tools like [UNFLoader](https://github.com/buu342/N64-UNFLoader) can debug over USB?

# libdragon ([Website](https://libdragon.dev/))
- [ ] Open source library for N64 development [GitHub](https://github.com/DragonMinded/libdragon) 
- [ ] **Download the *preview* branch!**
- [ ] Downloaded Toolchain Release **V16.2.0-31599716871** into `F:\Programs\libdragon`, which includes `mips64-elf-gcc.exe` and other compiler related .exe files, but not `n64tool.exe`. Added `F:\Programs\libdragon\bin` to `PATH`
- [ ] Need to build `n64tool` from source. I guess with [MSYS2](https://www.msys2.org/)?
- [ ] Installing MSYS2 from [Website](https://www.msys2.org/) into `C:/msys64/`
	- [ ] Opens a *UCRT64 environment* terminal
	- [ ] I guess we use `pacman` to install things?
	```sh
	$ pacman -S mingw-w64-ucrt-x86_64-gcc
	resolving dependencies...
	looking for conflicting packages...
	Packages (17) mingw-w64-ucrt-x86_64-binutils-2.46-4  mingw-w64-ucrt-x86_64-crt-14.0.0.r92.g818fa6510-1
	              mingw-w64-ucrt-x86_64-gcc-libs-16.1.0-5  mingw-w64-ucrt-x86_64-gettext-runtime-1.0-1
	              mingw-w64-ucrt-x86_64-gmp-6.3.0-2  mingw-w64-ucrt-x86_64-headers-14.0.0.r92.g818fa6510-1
	              mingw-w64-ucrt-x86_64-isl-0.27-1  mingw-w64-ucrt-x86_64-libiconv-1.19-1
	              mingw-w64-ucrt-x86_64-libwinpthread-14.0.0.r92.g818fa6510-1  mingw-w64-ucrt-x86_64-mpc-1.4.1-1
	              mingw-w64-ucrt-x86_64-mpfr-4.2.2-3  mingw-w64-ucrt-x86_64-tzdata-2026b-1
	              mingw-w64-ucrt-x86_64-windows-default-manifest-6.4-4  mingw-w64-ucrt-x86_64-winpthreads-14.0.0.r92.g818fa6510-1
	              mingw-w64-ucrt-x86_64-zlib-1.3.2-2  mingw-w64-ucrt-x86_64-zstd-1.5.7-2  mingw-w64-ucrt-x86_64-gcc-16.1.0-5
	Total Download Size:    68.98 MiB
	Total Installed Size:  490.23 MiB
	```
	- [ ] Installing `base-devel`, `mingw-w64-ucrt-x86_64-gcc`, `mingw-w64-ucrt-x86_64-make`, and `git`:
	```sh
	$ pacman -S base-devel mingw-w64-ucrt-x86_64-gcc mingw-w64-ucrt-x86_64-make git
	warning: mingw-w64-ucrt-x86_64-gcc-16.1.0-5 is up to date -- reinstalling
	resolving dependencies...
	looking for conflicting packages...
	Packages (50) binutils-2.46-2  bison-3.8.2-5  diffstat-1.69-1  diffutils-3.12-1  dos2unix-7.5.6-1
	              flex-2.6.4-4  heimdal-7.8.0-5  heimdal-libs-7.8.0-5  libcbor-0.14.0-2
	              libedit-20240808_3.1-1  libfido2-1.17.0-1  m4-1.4.21-1  make-4.4.1-3
	              openssh-10.3p1-2  patch-2.7.6-3  perl-Authen-SASL-2.2000-1  perl-Clone-0.50-2
	              perl-Convert-BinHex-1.125-2  perl-Encode-Locale-1.05-2  perl-Error-0.17030-1
	              perl-File-Listing-6.16-1  perl-HTML-Parser-3.85-1  perl-HTML-Tagset-3.24-1
	              perl-HTTP-Cookies-6.11-1  perl-HTTP-Daemon-6.17-1  perl-HTTP-Date-6.06-1
	              perl-HTTP-Message-7.02-1  perl-HTTP-Negotiate-6.01-3  perl-IO-HTML-1.004-2
	              perl-IO-Socket-SSL-2.098-1  perl-IO-Stringy-2.113-3  perl-LWP-MediaTypes-6.04-2
	              perl-MIME-tools-5.517-1  perl-MailTools-2.22-1  perl-Net-HTTP-6.24-1
	              perl-Net-SMTP-SSL-1.04-2  perl-Net-SSLeay-1.96-1  perl-TermReadKey-2.38-8
	              perl-TimeDate-2.35-1  perl-Try-Tiny-0.32-1  perl-URI-5.34-1
	              perl-WWW-RobotRules-6.03-1  perl-http-cookiejar-0.014-1  perl-libwww-6.83-2
	              texinfo-7.2-3  texinfo-tex-7.2-3  base-devel-2024.11-1  git-2.54.0-1
	              mingw-w64-ucrt-x86_64-gcc-16.1.0-5  mingw-w64-ucrt-x86_64-make-4.4.1-4
	Total Download Size:    21.22 MiB
	Total Installed Size:  305.09 MiB
	Net Upgrade Size:      120.87 MiB
	```
	- [ ] Set `N64_INST` environment variable to `F:\Programs\libdragon`
	- [ ] `cd /c/gamedev/downloaded/libdragon` and `./build.sh`
- [ ] `get_tv_type()` returns `TV_PAL`, `TV_NTSC`, or `TV_MPAL`. On SC64 in M64 console, it returns `TV_NTSC`
- [ ] **RDPQ** = **R**eality **D**isplay **P**rocess (command) **Q**ueue
- [ ] Building GCC Toolchain on MacOS
	- [ ] `export N64_INST="/opt/libdragon"`
	- [ ] `cd libdragon/tools`
	- [ ] `./build-toolchain.sh`
- [ ] 

# Emulators
- [ ] [RetroPie](https://retropie.org.uk/) [Github](https://github.com/RetroPie) 
- [ ] 
### BizHawk
- [ ] [GitHub Releases](https://github.com/TASEmulators/BizHawk/releases) 
- [ ] [Emulator Zone Page](https://www.emulator-zone.com/misc/bizhawk) 
- [ ] Linux x86_64 release, but .tar.gz contains .exe files?
### Project64
- [ ] [Website](https://www.pj64-emu.com/) 
- [ ] [GitHub](https://github.com/project64/project64) 
- [ ] [Emulator Zone Page](https://www.emulator-zone.com/doc.php/n64/project64.html) 
- [ ] Windows only?
### Mupen64++ / Mupen64 / mupen64plus
- [ ] [Website](https://mupen64plus.org/) 
- [ ] [GitHub](https://github.com/mupen64plus/mupen64plus-core/) 
- [ ] [Emulator Zone Page](https://www.emulator-zone.com/doc.php/n64/mupen64plusplus.html) 
- [ ] Linux x86_64 release. ==TODO:== Maybe I can compile for ARM64 Linux from source?
- [ ] RetroArch (inside Lakka) uses Mupen emulator for N64
### RetroArch
- [ ] [Website](https://www.retroarch.com/) 
- [ ] [Emulator Zone Page](https://www.emulator-zone.com/misc/retroarch) 
- [ ] Recommends [Lakka](https://www.lakka.tv/) sister project for running on Raspberry Pi. [rpi Downloads](https://www.lakka.tv/get/linux/rpi/) (Installed on 64GB SD Card)
### UltraHLE / UltraHLE 2064
### Simple64
### Gopher64
### Ares
- [ ] [Website](https://ares-emu.net/) 
- [ ] **This works!**
### Daedalus
### 1964
### SupraHLE