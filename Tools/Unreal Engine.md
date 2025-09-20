## General Notes
- [ ] **UE Version**: 5.4.4 (downloaded March 23rd 2025) Installed in `F:\Programs\UE` 35.7GB - 198,509 files - 42,447 folders
      ![[Unreal Engine 5.4.4 Install WizTree Visualization.png]]
- [ ] Getting Access to UE Github: [Link](https://www.unrealengine.com/en-US/ue-on-github) [Github](https://github.com/EpicGames/UnrealEngine)
- [ ] [Smart Pointer Types](https://dev.epicgames.com/documentation/en-us/unreal-engine/smart-pointers-in-unreal-engine) (Doesn't work with `UObject` which is tracked by a separate system)
	- [ ] **Shared Pointer `TSharedPtr`**: Keeps the object alive, deletes object when all shared pointers are destroyed
	- [ ] **Shared Reference `TSharedRef`**: Guarantees non-null value, similar to Shared Pointer otherwise
	- [ ] **Weak Pointer `TWeakPtr`**: Doesn't guarantee object is alive, the object can become null at any moment. But you can get a Shared Reference from a WeakReference and then free it to guarantee it stays alive for some temporary block
	- [ ] **Unique Pointer `TUniquePtr`**: Manages the lifetime of an object, no other smart pointer can reference it
- [ ] [Low-Level Memory Tracker (LLM)](https://dev.epicgames.com/documentation/en-us/unreal-engine/using-the-low-level-memory-tracker-in-unreal-engine) `LowLevelMemoryTracker.h`
	- [ ] *Default Tracker* shows all memory allocation made by the engine (like through `FMemory.Malloc` e.g `OnLowLevelAlloc`), see `stat LLM` and `stat LLMFULL`
	- [ ] *Platform Tracker* is lower level and tracks allocations made internal to OS level functions like `Binned2` (it's a strict subset of the Default Tracker)
	- [ ] All allocations are assigned a **single** group
	- [ ] "tag-scope" macros specify areas where any allocation within will be assigned to a specified group like `LLM_SCOPE_BYTAG` (`LLM_DECLARE_TAG` and `LLM_DEFINE_TAG`)
	- [ ] [Unreal Insights](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-insights-in-unreal-engine) Is the go-to profiler for UE
	- [ ] LLM is completely compiled out in *Test* and *Shipped* builds
- [ ] `PlayerStart` spawns a `DefaultPawn` at game start?
- [ ] *HLOD* = Hierarchical Level of Detail
- [ ] [Parent Classes in Unreal Engine](https://vrealmatic.com/unreal-engine/classes)
- [ ] 
## Tutorials
- [x] [Unreal Engine C++ Tutorial: Plugins](https://www.youtube.com/watch?v=mgFrFdzb7hg)
- [ ] [Unreal Motion Graphics (UMG)](https://dev.epicgames.com/documentation/en-us/unreal-engine/umg-ui-designer-quick-start-guide-in-unreal-engine)
- [ ] 
## Hotkeys
- [ ] **Q/W/E/R** - Select/Translate/Rotate/Scale Tool
- [ ] **Alt+P** - Play Game
- [ ] **Escape** - Stop Game
- [ ] **F8** - Toggle Play/Editor Focus
- [ ] **Shift+F1** - Stop mouse capture while playing
- [ ] **Ctrl+Space** - Open Content Drawer
- [ ] **Ctrl+P** - Open Asset Dialog (much faster than using Content Drawer)
- [ ] **F4** - Focus Content Drawer Path Textbox
- [ ] **Tilde** - Focus Console input
- [ ] **Alt+Tilde** - Open Output Log Drawer
- [ ] **Right Click + WASD/E/Q/Ctrl/Space** - First Person Fly Cam controls in Perspective viewport
- [ ] **H** - Hide Selected (doesn't work on Folders)
- [ ] **Shift+H** - Show Selected (doesn't work on Folders)
- [ ] **Ctrl+H** - Show All Hidden
- [ ] **Ctrl+Tilde** - Toggle between World and Object Gizmo Coordinates
- [ ] **Ctrl+Shift+P** - "Pilot" the selected actor(s)
- [ ] **Alt+1/2/3/4/5/6...** - Change to Wireframe/Unlit/Lit/Light Detail/etc. view modes in main panel
- [ ] **F** - Frame Selected Actor (Also added **Numpad Period** which moves to raycast location under mouse)
- [ ] **Ctrl+LeftClick/RightClick/BothClick** - Move/Rotate/Scale selected object along X/Y/Z axis without finding/clicking on the gizmo
- [ ] **Shift+LeftClick/RightClick (on Property)** - Copy/Paste property value (or category!) in Details Panel
- [ ] 
## Console Commands
- [ ] `stat LLM` and `stat LLMFULL` - commands show allocations made in the "Default Tracker" (aka `FMemory.Malloc`)
- [ ] `open [URL]` - Opens a particular map, or connects to a server at a particular address
- [ ] 
## Plugins
- [ ] **Fab** [Link](https://www.fab.com/) - Download plugins inside the Editor
- [ ] **Quixel Bridge** [Link](https://quixel.com/) - Download high quality scanned assets, aka "Megascans"
- [ ] 
## Classes
- [ ] `APawn` <- `AActor` <- `UObject` <- `UObjectBaseUtility` <- `UObjectBase`
    Possession <- Placeable/Components <- Designated Union (UClass) <- Utility Funcs <- Low Level Implementation
- [ ] 
## Unreal Build Related Systems
- [ ] Unreal Build System was a thing in UE4, now we have Unreal Build Tool, Unreal Header Tool, and Automation Tool
### Unreal Build Tool (UBT) [Link](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-build-tool-in-unreal-engine?application_version=5.5)
- [ ] Configured with `BuildConfiguration.cs`
- [ ] Builds UE source code
- [ ] Split into **modules** each module has a `.build.cs` file that determines how it builds
- [ ] By default modules compile to `.dll`s but you can choose to build a monolithic executable too
- [ ] UE is built without using the `.sln` or `.vcproj` files. These files are generated by `GenerateProject.bat`
- [ ] Run static analysis tools with `Engine\Build\BatchFiles\RunUBT.bat TARGET PLATFORM Development -StaticAnalyzer=ANALYZER`
### Unreal Header Tool (UHT) [Link](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-header-tool-for-unreal-engine)
- [ ] Handles parsing C++ header files and generating code for Unreal's `UObject` system
- [ ] Usually not run by the user, it's run automatically from UBT
- [ ] `RunUBT -Mode=UnrealHeaderTool "<PROJECT_FILE>" "<MANIFEST_FILE>"`
### Unreal Automation Tool (UAT) [Link](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-automation-tool-overview-for-unreal-engine)
- [ ] A host program and set of utility libraries that help you run unattended operations in C#
- [ ] Basically it's the framework for running things on the farm
- [ ] When run it finds and compiles all `.Automation.csproj` projects and uses reflection to find classes derived from `BuildCommand`
- [ ] BuildGraph scripts are written in XML, it's like a hybrid between Makefiles and a build-farm configuration script
- [ ] Visual Studio will use schema to provide rich tooltips when editing build graph xml files ``[Unreal Engine Root Directory]/Engine/Build/Graph/Schema.xsd`
- [ ] [BuildGraph link](https://dev.epicgames.com/documentation/en-us/unreal-engine/buildgraph-for-unreal-engine)
### Unreal Build Accelerator (UBA) [Link](https://dev.epicgames.com/documentation/en-us/unreal-engine/horde-unreal-build-accelerator-and-remote-compilation-tutorial-for-unreal-engine)
- [ ] This is basically SNDBS for UBT
- [ ] A tool included with Horde that implements lightweight virtualization for third-party programs (such as C++ compilers)
- [ ] Also supports compiling shaders
- [ ] Rolled out in 2024
- [ ] 
### Horde
- [ ] This is a specific set of tools that Epic uses to build their games and engine
- [ ] It's been used to ship Fortnite since 2021 but it was beta in UE 5.4 and production ready in UE 5.5
- [ ] Horde offers the following functionality, most of which can be enabled or disabled independently:
	- **Remote Execution**: Functionality to offload compute work to other machines, including C++ compilation with [Unreal Build Accelerator](https://dev.epicgames.com/documentation/en-us/unreal-engine/horde-unreal-build-accelerator-and-remote-compilation-tutorial-for-unreal-engine).
	- **Build Automation (CI/CD)**: A build automation system designed for teams working with large Perforce repositories.
	- **Test Automation**: A frontend for querying automation results across streams and projects, integrated with [Automation Tool](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-automation-tool-for-unreal-engine) and [Gauntlet](https://dev.epicgames.com/documentation/en-us/unreal-engine/gauntlet-automation-framework-in-unreal-engine).
	- **Studio Analytics**: Received telemetry from Unreal Editor and shows charts for key workflow metrics.
	- **UnrealGameSync Metadata Server**: Various features for teams using [UnrealGameSync](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-game-sync-ugs-for-unreal-engine), including build status reporting, comment aggregation, and crowdsourced build health functionality.
	- **Mobile/Console Device Manager**: A system for allocating and managing a farm of development kits and mobile devices.
![[UnrealEngine_HordeCircleDiagram.png]]
![[UnrealEngine_HordeLayersDiagram.png]]
- [ ] Unrealfest 2024 Talk about Horde: [Link](https://dev.epicgames.com/community/learning/talks-and-demos/9dP9/unreal-engine-horde-and-unreal-build-accelerator-operating-at-epic-scale-unreal-fest-2024)
- [ ] 
### Unreal Game Sync (UGS) [Link](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-game-sync-ugs-for-unreal-engine)
- [ ] UGS provides a graphical front-end to sync UE projects from **Perforce**, optionally building those projects with MSVC
- [ ] Basically it's something like VirtualSync?
- [ ] 