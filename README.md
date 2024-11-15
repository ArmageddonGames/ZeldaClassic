# Zelda Classic
Zelda Classic is a game and editing tool that lets you create custom Legend of Zelda quests.

Homepage:
http://zeldaclassic.com

The homepage contains information about the latest release, links to the latest binaries, and a repository of custom quests for you to enjoy. 

This repository contains the Zelda Classic source code, for use by the Zelda Classic developers and advanced users wanting to port ZC to new platforms. You do not need to download or compile the source if you want to play Zelda Classic or make quests on Windows, OS X, or (Debian) Linux.

### Screenshots

<img src="screenshots/demo.png"> <img src="screenshots/lost1.png"> <img src="screenshots/lost2.png"> 
<img src="screenshots/saffith.png"> <img src="screenshots/di.png"> <img src="screenshots/zoria.png"> 
<img src="screenshots/tort.png"> <img src="screenshots/heavens.png">

<img src="screenshots/editor1.png" width="400" height="300"> <img src="screenshots/editor2.png" width="400" height="300">

## Special Thanks

A special thanks to all the past developers, contributors, testers, and content creators over the long and rich history of Zelda Classic that began as a simple editable LOZ clone back in 1999. Many of whom have moved on to other endevours or are sadly no longer with us. Thank You.

## About this Repository

This repository was resurrected and reconstructed after the theft of the original Zelda Classic repository.<br/>
Let this epitaph stand as a reminder for all of the scourge of the adherants to the church of moral relativism and their false idols and doctrines.

- *“If ye love wealth better than liberty, the tranquility of servitude better than the animating contest of freedom, go home from us in peace. We ask not your counsels or arms. Crouch down and lick the hands which feed you. May your chains set lightly upon you, and may posterity forget that ye were our countrymen.”* ― Samuel Adams

- *Every way of a man is right in his own eyes; but the LORD weigheth the hearts.* ― (Proverbs 21:2)
- *The getting of treasures by a lying tongue is a vapour driven to and fro; they seek death.* ― (Proverbs 21:6)
- *The soul of the wicked desireth evil; his neighbour findeth no favour in his eyes. ... When the scorner is punished, the thoughtless is made wise; and when the wise is instructed, he receiveth knowledge.* ― (Proverbs 21:10)
- *To do justly is joy to the righteous, but ruin to the workers of iniquity.* ― (Proverbs 21:15)
- *He that followeth after righteousness and mercy findeth life, prosperity, and honour.* ― (Proverbs 21:21)
- *A proud and haughty man, scorner is his name, even he that dealeth in overbearing pride.* ― (Proverbs 21:24)
- *There is that coveteth greedily all the day long; but the righteous giveth and spareth not.* ― (Proverbs 21:26)
- *A false witness shall perish; but the man that obeyeth shall speak unchallenged.* ― (Proverbs 21:28)

## Building the Source

Because of Zelda Classic's extended development history and dependency on legacy libraries, the build process is somewhat involved. The instructions here are not comprehensive, but are intended to help you get started.

### General Comments

**1))** Zelda Classic uses CMake to build the source. Before getting started, you will need to install CMake (version 3.5 or later.) The scripts have been tested on the following operating systems and toolchains:

- **Windows XP with MSVC 2008**
- **Windows 10 with MSVC 2015**
- **Ubuntu 16.04 with g++ 5.4**

You may need to tweak the configuration settings for other platforms.

**2))** The Zelda Classic project includes three executables and one library:
 - the zcsound library, which is used by all the other binaries;
 - zelda, the Zelda Classic player;
 - zquest, the Zelda Classic level editor;
 - romview, a utility for ripping tiles from SNES ROMs.
 
The included build scripts will build all four targets.

**3))** Included in this repository are pre-built libraries for many of ZC's dependencies, including Allegro and several Allegro add-on libraries for handling sound. These binaries are included for the most common platforms for convenience of the developers, but if you are using a different operating system or toolchain you may need to rebuild these binaries from source. There are (currently) no automated scripts for doing this, but the source packages are included in the `/other` directory.

Zelda Classic requires a modified version of the Allegro 4.2.2 library. Again, pre-built library binaries are available in `/libs`, and if you need to rebuild the library from source, it is contained in `./allegro/fixed/all422-fixed.zip`. A stripped-down version of the fixed library, containing only the header files needed to compile ZC, is in `./allegro`. **Do not try to link Zelda Classic against the standard 4.2.2 Allegro library. You must use the pre-built binaries, or the modified source.**

**4))** Zelda Classic works **only** when compiled for a 32-bit architecture (but the compiled binaries will run fine on 64-bit operating systems.) This means that to successfully compile ZC, you must set your compiler to generate 32-bit code, and you must **obtain 32-bit versions of all external libraries** (or build them yourself from source). For example, on 64-bit Ubuntu you may need to install the packages g++-multilib, libx11-dev:i386, libxext-dev:i386, libxcursor-dev:i386, libxxf86vm-dev:i386, libxpm-dev:i386, libasound2-dev:i386, and possibly others. If you are getting linker errors, check carefully for messages about binary incompatibility with the external libraries.

**5))** The ZScript parser included with ZQuest uses Flex and Bison to auto-generate its source code. You must download and install Flex and Bison to compile ZQuest with ZScript support. If you do not have these tools, compilation will not fail, but CMake will issue a warning and your ZQuest binary will be compiled without the ability to compile ZScripts.

For Windows user, win-flex and win-bison will work fine. Be sure to add the folder containing the binaries (e.g. `win-flex.exe`) to your PATH environment variable.

CMake will issue a warning if it cannot find Flex or Bison on your system.

### Quick-start: Windows with MSVC

Download CMake and run the CMake GUI. It will prompt your for the location of the source code, and the location in which to build the binaries. Specify the root (the folder containing this file) for the former and the `build` folder for the latter.

Click "Generate." This will create a Visual Studio project file for you in the build directory. You can then open up the project file in MSVC and do editing/compilation/debugging in MSVC. You do not need to touch CMake again unless you want to change project configuration options or add/remove source files.

### Quick-start: Linux with gcc

Ensure you have CMake 3.5+ install and execute the following commands:
```
cd build
cmake ..
make
```

Binaries will be created in the `build` folder.

## Running the Compiled Binaries

The compiled binaries **will not run** on their own without support files. These files are not (currently) included in this repository, due to copyright concerns. To run the compiled source, download the latest binary package from the project homepage, and copy the binaries from `build` into a folder also containing all of the data files from the binary package.

## Contributing to Zelda Classic

We encourage third-party submission of patches and new features! If you're interesting in contributing to Zelda Classic's development, please read the CONTRIBUTE file.

## License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.


