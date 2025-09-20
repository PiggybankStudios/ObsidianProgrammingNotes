# Notes
- [ ] [Download Android Studio](https://developer.android.com/studio)
- [ ] [APK Analyzer](https://developer.android.com/studio/debug/apk-analyzer) (`.apk` files can be found in places like `app\build\intermediates\apk\` in an Android Studio project)
- [ ] NDK Version: **29.0.13599879** (`F:\Programs\android_studio_sdk\ndk\29.0.13599879\` on Desktop)
- [ ] [Android Gradle API](https://developer.android.com/reference/tools/gradle-api/8.13/classes)
- [ ] [Build your app from the command line](https://developer.android.com/build/building-cmdline) [StackOverflow](https://stackoverflow.com/questions/32643297/how-to-make-an-android-app-without-using-android-studio)
- [ ] [Android SDK Command-line Tools](https://developer.android.com/tools/)
- [ ] [Command-line Tools Download](https://developer.android.com/studio/index.html#command-line-tools-only)
- [ ] [Using Android 8 and 9 Emulators Without Android Studio](https://www.andreszsogon.com/using-android-8-and-9-emulators-without-android-studio/)
- [ ] [JNI Functions](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/spec/functions.html)
- [ ] [Signing your app](https://developer.android.com/studio/publish/app-signing) 
- [ ] [Android NDK](https://developer.android.com/ndk/guides) [NDK Samples](https://github.com/android/ndk-samples) [Install Guide](https://developer.android.com/studio/projects/install-ndk)
	- In Android Studio: **Tools->SDK Manager->SDK Tools->NDK (Side by Side)** (Enable Show Package Details to see specific NDK versions)
- [ ] [Java Native Interface (JNI)](https://docs.oracle.com/javase/7/docs/technotes/guides/jni/spec/jniTOC.html)
- [ ] [Install and Configure NDK and Cmake](https://developer.android.com/studio/projects/install-ndk)
- [ ] **ndk-build.cmd** is at `F:\Programs\android_studio_sdk\ndk\29.0.13599879\`
	- [ ] `%NDK%\ndk-build -C ..`
	- [ ] Builds a [JSON Compilation Database](https://clang.llvm.org/docs/JSONCompilationDatabase.html)
- [ ] **cmake** is at `F:\Programs\android_studio_sdk\cmake\4.1.1\`
	- [ ] By default a project will use a forked cmake `v3.6.0` unless specified otherwise in `build.gradle`: `android { externalNativeBuild { cmake { version "version" } } }`
- [ ] [16kB Page Alignment Requirement](https://developer.android.com/guide/practices/page-sizes)
	- [ ] Add this to **CMakeLists.txt**: `target_link_libraries(native-lib LINKER:-z,max-page-size=16384)`
- [ ] After changing `build.gradle` you will have to click ![[AndroidStudioSyncProjectWithGradleFiles.png]] before the Run button is available again
- [ ] [Create an Android library](https://developer.android.com/studio/projects/android-library): Create an `.aar` file rather than `.apk` that can be depended on by an `.apk`
- [ ] Can compile with `{NDK}/sources/android/native_app_glue/android_native_app_glue.c` which helps the native module not block the main activity thread when it's handling events.
- [ ] C/C++ Module runs in it's own thread, not the main thread? The thread needs to be associated with Java VM before JNI calls can be made ==(TODO: Double check this)==
- [ ] **NOTE:** In C the `JNIEnv` is defined as a pointer to `JNINativeInterface` and is often passed to you like `JNIEnv*` which means we need to double-dereference it to access functions. That means we do something like `(*env)->NewStringUTF("Hello Android")`
- [ ] We have to compile our native library to both `arm64-v8a` and `x86_64` (and optionally `armeabi-v7a` folder older device support). `x86_64` is used by the android Virtual Device so we need it for testing on the computer (clang targets are `aarch64-none-linux-android35`, `armv7a-none-linux-androideabi35`, and `x86_64-none-linux-android35`)
- [ ] `--sysroot` must be set to `%NDK_DIR%/toolchains/llvm/prebuilt/windows-x86_64/sysroot`
- [ ] `gradlew.bat build` runs the following: `"C:\Program Files\Eclipse Adoptium\jdk-17.0.7.7-hotspot\/bin/java.exe" "-Xmx64m" "-Xms64m" "-Dorg.gradle.appname=gradlew" -classpath "F:\gamedev\projects\_android\Sputnik\\gradle\wrapper\gradle-wrapper.jar" org.gradle.wrapper.GradleWrapperMain build`
- [ ] Apparently we **have** to have a `classes.dex` inside our `.apk` which means we need a dummy Java/Kotlin class that we compile and insert just so Android is happy
- [ ] `printf` does not seem to be routed anywhere (as far as I can tell), and I can't find any info on options to the Android SDK stdlib to make it route somewhere
- [ ] JNI type signature strings include the following types (For example when calling `GetMethodID` on a `jclass`):
	- [ ] `Z`: boolean
	- [ ] `B`: byte
	- [ ] `C`: char
	- [ ] `S`: short
	- [ ] `I`: int
	- [ ] `J`: long
	- [ ] `F`: float
	- [ ] `D`: double
	- [ ] `L fully_qualified_class`: `fully_qualified_class`
	- [ ] `[ type`: `type[]`
	- [ ] `( arg_types ) return_type`: Method with `arg_types` and `return_type`
- [ ] Martins Comment in [Starting with mobile dev the right way](https://discord.com/channels/239737791225790464/1268141449699135550/1268141449699135550) (also see [Build android native app together with Java code](https://discord.com/channels/239737791225790464/1291659542739947530/1291659542739947530))
> having JNIEnv created for thread comes with implications
   for example, your thread can be interrupted by runtime garbage collector
   if you don't have JNIEnv, then thread does not need to be interrupted
   which can sometimes be important, like for audio thread
- [ ] In Android emulator you can hold **Ctrl+LeftClick** to simulate 2 touch rotational movements. Or **Ctrl+RightClick** to simulate 2 touch drag movements
- [ ] 
---
# Gradle Notes
- [ ] `gradlew.bat` in an Android Studio project just calls `java.exe` on `gradle/wrapper/gradle-wrapper.jar`
      `java.exe "-Xmx64m" "-Xms64m"   "-Dorg.gradle.appname=gradlew" -classpath "gradle\wrapper\gradle-wrapper.jar" org.gradle.wrapper.GradleWrapperMain build`
- [ ] We can use [Vineflower](https://vineflower.org/usage/) to decompile the `gradle-wrapper.jar`
- [ ] There's also a `gradle-wrapper.properties` file next to the `.jar` that gets loaded by the wrapper:
	```
	distributionBase=GRADLE_USER_HOME
	distributionPath=wrapper/dists
	distributionUrl=https\://services.gradle.org/distributions/gradle-8.13-bin.zip
	zipStoreBase=GRADLE_USER_HOME
	zipStorePath=wrapper/dists
	```
- [ ] The wrapper finds the `GRADLE_HOME` path and runs `lib/gradle-launcher-.*\.jar` looking for `org.gradle.launcher.GradleMain` inside (which actually seems to be inside `gradle-gradle-cli-8.13.jar` which I think is loaded by the main launcher .jar through the `META-INF/MANIFEST.MF`)
- [ ] The wrapper seems to automatically download Gradle if it doesn't find it installed
- [ ] Gradle is a build system that primarily runs the following CLI tools: `aapt2`, `javac` or `kotlinc`, `d8`, `apksigner`, `zipalign` (See **Build CLI Tools** section below)
- [ ] Default debug keystore is located at `%USERPROFILE%/.android/debug.keystore`. Password is `android`
- [ ] 
---
# Sputnik App
- [ ] API 24 "Nougat" Android 7.0
- [ ] Build configuration language: `Kotlin DSL`
- [ ] Language: `Kotlin`
- [ ] Package: `com.piggybank.sputnik`
- [ ] To get things working, comment out `include(":app")` line in `settings.gradle.kts`, then **File->Sync Project with Gradle Files**, then uncomment it and sync again.
- [ ] SDK Install Folder:
	- Desktop: `F:\Programs\android_studio_sdk\`
	- Laptop: `D:\Programs\android_sdk\`
- [ ] MapView added to fragment required the library `com.google.android.gms:play-services-maps`. This edited `gradle/libs.versions.toml`
- [ ] 
---
# Hotkeys
- [ ] `Shift - Shift`: Search?
- [ ] `Ctrl+Alt+S`: Open Settings
- [ ] `Alt+Shift+Left/Right`: Expand/Collapse Code View while looking at files that have a "Designer" view
- [ ] `Shift+F10`: Run App
- [ ] `Shift+F9`: Debug App
- [ ] `Ctrl+Shift+O`: Sync Project with Gradle Files
- [ ] `Ctrl+Shift+B/H/W`: In Virtual Device - Back/Home/Apps
- [ ] `Ctrl+Space`: Auto-complete (in Logcat Search)
---
# Android Versions
%% These are usually all named after desserts %%
- [ ] API 21 "Lollipop" Android 5.0
- [ ] API 22 "Lollipop" Android 5.1
- [ ] API 23 "Marshmallow" Android 6.0
- [ ] API 24 "Nougat" Android 7.0
- [ ] API 25 "Nougat" Android 7.1
- [ ] API 26 "Oreo" Android 8.0
- [ ] API 27 "Oreo" Android 8.1
- [ ] API 28 "Pie" Android 9.0
- [ ] API 29 "Q" Android 10.0
- [ ] API 30 "R" Android 11.0
- [ ] API 31 "S" Android 12.0
- [ ] API 32 "Sv2" Android 12L
- [ ] API 33 "Tiramisu" Android 13.0
- [ ] API 34 "UpsideDownCake" Android 14.0
- [ ] API 35 "VanillaIceCream" Android 15.0
- [ ] **API 36 "Baklava" Android 16.0**
### Taylor's Phone (Galaxy ZFold5)
- [ ] API 33 "Tiramisu" Android 13.0
- [ ] One UI 5.1.1
- [ ] 
---
# Build CLI Tools
Found in `[ANDROID_SDK]/build-tools/[Version]/`
### aapt2
Android Asset Packaging Tools
**Usage:** `aapt2 [subcommand] [options] files...`
- [ ] `compile`:  Compiles resources to be linked into an apk
	- [ ] `-o [path]`: Output path
	- [ ] `--dir [path]`: Directory to scan for resources
	- [ ] `--zip [path]`: Zip file containing the res directory to scan for resources
	- [ ] `-v`: Enables verbose logging
- [ ] `link`:  Links resources into an apk
	- [ ] `-o [path]`: Output path
	- [ ] `--manifest AndroidManifest.xml`: Path to the Android manifest to build
	- [ ] `-I arg`: Adds an Android APK to link against
	- [ ] `-A arg`: An assets directory to include in the APK (These are unprocessed)
	- [ ] `-R arg`: Compilation unit to link, using 'overlay' semantics
	- [ ] `-c [configs]...`: A comma-separated list of configurations to include, the default is all configurations
	- [ ] `-v`: Enables verbose logging
- [ ] `dump`: ?
	- [ ] `apc: ?
	- [ ] `badging`: ?
	- [ ] `configurations`: ?
	- [ ] `packagename`: ?
	- [ ] `permissions`: ?
	- [ ] `strings`: ?
	- [ ] `styleparents`: ?
	- [ ] `resources`: ?
	- [ ] `chunks`: ?
	- [ ] `xmlstrings`: ?
	- [ ] `xmltree`: ?
	- [ ] `overlayable`: ?
- [ ] `diff`: Prints the differences in resources of two apks
- [ ] `optimize`: Preforms resource optimizations on an apk
- [ ] `convert`: Converts an apk between binary and proto formats
- [ ] `version`: Prints the version of aapt
- [ ] `apkinfo`: Dump information about an APK in binary proto format
- [ ] `daemon`: Runs aapt in daemon mode. Each subsequent line is a single parameter to the command. The end of an invocation is signaled by providing an empty line
### apksigner (apksigner.bat calls lib/apksigner.jar)
Signs or checks signage of `.apk` files
**Usage:** `apksigner <command> [options]`
**Example:** `apksigner sign --ks release.jks app.apk`
- [ ] `rotate`
- [ ] `sign`
	- [ ] **Usage:** `apksigner sign --ks %USERPROFILE%/.android/debug.keystore app.apk`
- [ ] `verify`
- [ ] `lineage`
- [ ] `version`
- [ ] `help`
### zipalign
Zip alignment utility
**Usage:** `zipalign [-f] [-p] [-P <pagesize_kb>] [-v] [-z] <align> infile.zip outfile.zip`
		`zipalign -c [p] [-P <pagesize_kb>] [-v] <align> infile.zip`
- [ ] `-c`: Check alignment only (does not modify file)
- [ ] `-f`: overwrite existing `outfile.zip`
- [ ] `-p`: 4kb page-align uncompressed .so files
- [ ] `-v`: verbose output
- [ ] `-z`: recompress using Zopfli
- [ ] `-P <pagesize_kb>`: Align uncompressed .so files to the specified page size. Valid values for `<pagesize_kb>` are 4, 16 and 64. `-P` cannot be used in combination with `-p`
### javac
Java compiler (to `.class` files)
**Usage:** `javac <options> <source files>`
- [ ] `-g`: Generate all debugging info (See `-g:{lines,vars,source,none}` for partial or no debug info)
- [ ] `-verbose`:  Output messages about what the compiler is doing
- [ ] `-version`: Version information
- [ ] `-Werror`: Terminate compilation if warnings occur
### kotlinc
Kotlin Compiler (to `.class` files?)
- [ ] ==TODO:==: Do we need to compile any Kotlin code for `NativeActivity`?
### d8 (d8.bat calls lib/d8.jar)
Compiles `.class` files to `.dex` files that can be added to `.apk` with `aapt2 add app.apk classes.dex` ==TODO:== Is this supposed to be `link` instead of `add`?
- [ ] ==TODO:== Do we need this if we are doing `NativeActivity`?
# Android Virtual Device (AVD) Emulator CLI
Found in `[ANDROID_SDK]/emulator/` (`adb.exe` is actually in `[ANDROID_SDK]/platform-tools/`)
### emulator.exe
- [ ] `-list-avds`: Lists all available Virtual Devices
- [ ] `-avd <name>`/`@<name>`: Run a particular Android Virtual Device by name
- [ ] `-avd-arch <target>`: Use a specific target architecture
- [ ] `-sysdir <dir>`: Search for system disk images in `<dir>`
- [ ] `-logcat-output <file>`: Output file of logcat (default is none)
- [ ] `-no-audio`: Disable audio support
- [ ] `-port <port>`: TCP port that will be used for the console
- [ ] `-no-boot-anim`: Disable animation for faster boot
- [ ] `-version`: Display emulator version number
- [ ] `-verbose`: Same as `-debug-init` (`-debug-<tag>` enable specific debug messages)
- [ ] 
### adb.exe (Android Debug Bridge)
`adb shell pm list packages`: List all installed packages (aka things like `com.piggybank.sputnik`)
`adb shell dumpsys package com.piggybank.sputnik`: ?
`adb install path/to/app.apk`: Install an .apk file onto the running AVD
#### Commands
- [ ] `devices [-l]`: List connected devices (`-l` for long output)
- [ ] `version`: Show version num
- [ ] `connect HOST[:PORT]`: ?
- [ ] `disconnect HOST[:PORT]`: ?
- [ ] `pair HOST[:PORT] [PAIRING CODE]`: ?
- [ ] `install [-lrtsdg] [--instant] PACKAGE`: Push a single package to the device and install it
	- [ ] `-r`: Replace existing application
	- [ ] `-t`: Allow test packages
	- [ ] `-d`: Allow version code downgrade (debuggable packages only)
	- [ ] `-p`: Partial application install (`install-multiple` only)
	- [ ] `-g`: Grant all runtime permissions
	- [ ] `--abi ABI`: Override platform's default ABI
	- [ ] `--instant`: Cause the app to be installed as an ephemeral install app
	- [ ] `--no-streaming`: Always push APK to device and invoke Package Manager as separate steps
	- [ ] `--streaming`: Force streaming APK directly into Package Manager
	- [ ] `--fastdeploy`: Use fast deploy
	- [ ] `--no-fastdeploy`: Prevent use of fast deploy
	- [ ] `--force-agent`: Force update of deployment agent when using fast deploy
	- [ ] `--date-check-agent`: Update deployment agent when local version is newer and using fast deploy
	- [ ] `--version-check-agent`: Update deployment agent when local version has different version code and using fast deploy
- [ ] `uninstall [-k] PACKAGE`: Remove this app package from the device
	- [ ] `-k`: Keep the data and cache directories
- [ ] `logcat [OPTION]... [FILTERSPEC]...`: Connect to an AVD and print out the logcat results
	- [ ] `-b BUFFER`: Request a ring buffer. Options are `main`, `system`, `radio`, `events`, `crash`, `default`, `all` (`kernel` for userdebug/eng builds, `security` for Device Owner installations)
	- [ ] `-c`: Clear (flush) the entire log and exit (can be used with `-f`)
	- [ ] `-d`: Dump the log and then exit (don't block)
	- [ ] `-L`: Dump logs from prior to last reboot from pstore
	- [ ] `-e`/`--regex=EXPR`: Only print lines matching ECMAScript regex `EXPR`
	- [ ] `-m`/`--max-count=N`: Exit after printing `N` lines
	- [ ] `--print`: With `--regex` and `--max-count`, prints all messages even if they do not match the regex, but exits after printing max-count matching lines.
	- [ ] `--pid=PID`: Only print logs from the given pid
	- [ ] `-v`/`--format=FORMAT`: Sets the log print format
	- [ ] `-D`/`--dividers`: Print dividers between each log buffer
	- [ ] `-B`/`--binary`: Print the log in binary
	- [ ] `-f`/`--file=FILE`: Log to FILE instead of stdout
	- [ ] `-r`/`--rotate-kbytes=N`: Rotate log every N KiB, requires `-f`
	- [ ] `-n`/`--rotate-count=N`: Sets the max number of rotated logs, default 4
	- [ ] `--id=<id>`: Clears the associated files if the signature `<id>` for logging to file changes
#### Options
- [ ] `-a`: Listen on all network interfaces, not just localhost
- [ ] `-d`: Use USB device (error if multiple devices connected)
- [ ] `-e`: Use TCP/IP device (error if multiple TCP/IP devices available)
- [ ] `-s SERIAL`: Use device with given serial (overrides $ANDROID_SERIAL)
- [ ] `-t ID`: Use device with given transport id
- [ ] `-H`: Name of the adb server host (default=localhost)
- [ ] `-P`: Part of the adb server (default=5037)
- [ ] `-L SOCKET`: Listen on the given socket for adb server (default=tcp:localhost:5037)
- [ ] `--one-device SERIAL|USB`: Only allows with `start-server` or `server nodaemon`, server will only connect to one USB device, specified by a serial number of USB device address
- [ ] `--exit-on-write-error`: Exit of stdout is closed
- [ ] 
