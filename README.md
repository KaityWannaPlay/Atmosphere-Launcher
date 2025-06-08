<H1 align="center">Atmosphere Launcher</H1>

[![Android CI](https://github.com/Vera-Firefly/Pojav-Glow-Worm/actions/workflows/main.yml/badge.svg)](https://github.com/Vera-Firefly/Pojav-Glow-Worm/actions)
![Downloads](https://img.shields.io/github/downloads/Vera-Firefly/Pojav-Glow-Worm/total)

* From [Boardwalk](https://github.com/zhuowei/Boardwalk)'s ashes here comes PojavLauncher!

* PojavLauncher is a launcher that allows you to play Minecraft: Java Edition on your Android device!

* It can run almost every version of Minecraft, allowing you to use .jar only installers to install modloaders such as [Forge](https://files.minecraftforge.net/) and [Fabric](http://fabricmc.net/), mods like [OptiFine](https://optifine.net) and [LabyMod](https://www.labymod.net/en), as well as hack clients like [Wurst](https://www.wurstclient.net/), and much more!

## Navigation
- [Introduction](#introduction)  
- [Building](#building) 
- [Current status](#current-status) 
- [License](#license) 
- [Contributing](#contributing) 
- [Credits & Third party components and their licenses](#credits--third-party-components-and-their-licenses-if-available)
- [More](#More)

## Introduction 
* PojavLauncher is a Minecraft: Java Edition launcher for Android based on [Boardwalk](https://github.com/zhuowei/Boardwalk). 
* This launcher can launch almost all available Minecraft versions ranging from rd-132211 to 1.21.x snapshots (including Combat Test versions). 
* Modding via Forge and Fabric are also supported. 
* This repository contains source code for Android. 
* Pojav Glow·Worm does not support IOS

## Getting Pojav Glow-Worm

You can get PojavLauncher via three methods:

1. You can get the prebuilt app from [stable releases](https://github.com/Vera-Firefly/Pojav-Glow-Worm/releases) or [automatic builds](https://github.com/Vera-Firefly/Pojav-Glow-Worm/actions).

2. You can [build](#building) from source.
## Building
If you want to build from source code, follow the steps below.
### Java Runtime Environment (JRE)
- JRE for Android is [here](https://github.com/Vera-Firefly/android-openjdk-build)
- Follow build instruction on build script [README.md](https://github.com/Vera-Firefly/android-openjdk-build/blob/buildjre8/README.md).
- You can also get [CI auto builds](https://github.com/Vera-Firefly/android-openjdk-autobuild/actions) if you are lazy or are failing to build it for some reason.
* Either get the `jre8-pojav` artifact from auto builds, or split all artifacts by yourself:</br>
   - Get JREs for all of 4 supported architectures (arm, arm64, x86, x86_64) </br> 
      - Split JRE into parts:</br>
                Platform-independent: .jar files, libraries, configs, etc...</br>
                Platform-dependent: .so files, etc...</br>
        - Create:</br>
                A file named `universal.tar.xz` with all platform-independent files</br>
                4 files named `bin-<arch>.tar.xz` with all platform-dependent files per-architecture</br>
        - Put these in the `assets/components/jre/` folder</br>
        - (If needed) update the Version file with the current date</br>

### LWJGL
* The build instructions for the custom LWJGL are available over the [LWJGL repository](https://github.com/PojavLauncherTeam/lwjgl3)

* This modified version of lwjgl uses the latest content from [Vera-Firefly](https://github.com/Vera-Firefly) [lwjgl3-build](https://github.com/Vera-Firefly/lwjgl3-build) repository for automated builds
### The Launcher
* Build GLFW stub (If need):
```
git submodule update --init --recursive
```
or
```
chmod +x scripts/UpdateSubmodule.sh
./scripts/UpdateSubmodule.sh
```
then run:
```
cd lwjgl3-build
./gradlew :jre_lwjgl3glfw:build
```
```
mv lwjgl3/* ../app_pojavlauncher/src/main/assets/components/lwjgl3
cd ../
```
* Build the launcher
```
./gradlew :app_pojavlauncher:assembleDebug
```
(Replace `gradlew` with `gradlew.bat` if you are building on Windows)
(If you are having trouble with `mv` permissions, try using `sudo mv`)

## Current status

- [ ] branding and other name related stuff (partly done now)
- [ ] revamp the ui
- [ ] better default renders
- [ ] alternative turnip selution for non adrenos
- [ ] Better java args by Default
- [ ] More to come!

## Known Issues
- Controller mods aren't working.
- Random crashes could happen very often on Android 5.x when loading the game or joining a world.
- With big modpacks textures could be messed up
- Probably more, that's why we have a bug tracker

## License
- Pojav Glow·Worm is licensed under [GNU GPLv3](https://github.com/Vera-Firefly/Pojav-Glow-Worm/blob/main_v3/LICENSE).

## Contributing
Contributions are welcome! We welcome any type of contribution, not only code. For example, you can help the wiki shape up. You can help the translation too!


Any code change to this repository should be submitted as a pull request. The description should explain what the code does and give steps to execute it.

## Credits & Third party components and their licenses (if available)
- [Pojav-Glow-Worm](https://github.com/Vera-Firefly/Pojav-Glow-Worm) (for creating source base): [GNU General Public License v3.0](https://github.com/Vera-Firefly/Pojav-Glow-Worm/blob/main/LICENSE)
- [Boardwalk](https://github.com/zhuowei/Boardwalk) (JVM Launcher): Unknown License/[Apache License 2.0](https://github.com/zhuowei/Boardwalk/blob/master/LICENSE) or GNU GPLv2.
- Android Support Libraries: [Apache License 2.0](https://android.googlesource.com/platform/prebuilts/maven_repo/android/+/master/NOTICE.txt).
- [GL4ES](https://github.com/PojavLauncherTeam/gl4es): [MIT License](https://github.com/ptitSeb/gl4es/blob/master/LICENSE).<br>
- [OpenJDK](https://github.com/PojavLauncherTeam/openjdk-multiarch-jdk8u): [GNU GPLv2 License](https://openjdk.java.net/legal/gplv2+ce.html).<br>
- [LWJGL3](https://github.com/PojavLauncherTeam/lwjgl3): [BSD-3 License](https://github.com/LWJGL/lwjgl3/blob/master/LICENSE.md).
- [LWJGLX](https://github.com/PojavLauncherTeam/lwjglx) (LWJGL2 API compatibility layer for LWJGL3): unknown license.<br>
- [Mesa 3D Graphics Library](https://gitlab.freedesktop.org/mesa/mesa): [MIT License](https://docs.mesa3d.org/license.html).
- [Android-Mesa-Build](https://github.com/Vera-Firefly/android-mesa-build): [GNU GPLv3 License](https://github.com/Vera-Firefly/android-mesa-build/blob/master/LICENSE)
- [TurnipDriver-CI](https://github.com/Vera-Firefly/TurnipDriver-CI): Unknown License
- [AdrenoToolsDrivers](https://github.com/K11MCH1/AdrenoToolsDrivers): Unknown License
- [pro-grade](https://github.com/pro-grade/pro-grade) (Java sandboxing security manager): [Apache License 2.0](https://github.com/pro-grade/pro-grade/blob/master/LICENSE.txt).
- [bhook](https://github.com/bytedance/bhook) (Used for exit code trapping): [MIT license](https://github.com/bytedance/bhook/blob/main/LICENSE).
- [libepoxy](https://github.com/anholt/libepoxy): [MIT License](https://github.com/anholt/libepoxy/blob/master/COPYING).
- [virglrenderer](https://github.com/PojavLauncherTeam/virglrenderer): [MIT License](https://gitlab.freedesktop.org/virgl/virglrenderer/-/blob/master/COPYING).
- [terminal-view](https://github.com/termux/termux-app/tree/master/terminal-view): [Apache 2.0](https://github.com/termux/termux-app/blob/master/LICENSE.md).
- [terminal-emulator](https://github.com/termux/termux-app/tree/master/terminal-emulator): [Apache 2.0](https://github.com/termux/termux-app/blob/master/LICENSE.md).
- Thanks to [MCHeads](https://mc-heads.net) for providing Minecraft avatars.

## More
* If you want a different experience, try some of the other good ones:[ZalithLauncher](https://github.com/ZalithLauncher/ZalithLauncher)

