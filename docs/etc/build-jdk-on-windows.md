# Let me teach you how to build OpenJDK on Windows

I choose 17 LTS, OpenJDK, which is the original source of all the other distributions, for a specific reason.  

I did this because I need to change some java base classes and can't find any simple way while trying to get a CC certification for what I'm working on.  

It's simple on `JDK 8`, but **it's not that simple after that.**

## Goals

- [x] Modify OpenJDK source code(Above JDK 9)
- [x] Build OpenJDK on Windows
- [x] Can build various distributions of OpenJDK

## Prerequisites

- Compiler/Toolchain [Visual Studio Community Edition](https://wiki.openjdk.org/display/Build/Supported+Build+Platforms)
- Option 1. [Cygwin](https://cygwin.com/install.html)
  - `setup-x86_64 -q -P autoconf -P make -P unzip -P zip`
- Option 2. [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
- [Choose which JDK versions you want to build](https://whichjdk.com/)
  - [OpenJDK 17](https://github.com/openjdk/jdk17u.git)
  - [Amazon Corretto 17](https://github.com/corretto/corretto-17)
  - **[JetBrains Runtime](https://github.com/JetBrains/JetBrainsRuntime)** - I recommend this one if you don't have any idea which one to choose because it's easy to build compared to others.
  - I tried the above 3 distributions and succeeded all on Cygwin, but only succeeded on JetBrains Runtime on WSL.

## Precautions
- [X] **Boot JDK Requirements**: [so for building JDK 9 a JDK 8 would be suitable as boot JDK.](https://openjdk.org/groups/build/doc/building.html)

## Using Cygwin  
- [X] **Install Boot JDK on Windows**
- [X] **Set `JAVA_HOME` environment variable on Windows**
- [X] **Set `PATH` environment variable on Windows**
- [X] **Clone OpenJDK source code**: ```git clone https://github.com/openjdk/jdk17u.git```
- [ ] **Mod OpenJDK source code** - make changes to the source code you want to modify
- [X] **Add excute permission to configure**: ```chmod +x configure```
- [X] **Remove `-Werror` in `./make/langtools/build.properties` and `./make/autoconf/flags-cflags.m4`** affecting your build. I tried to solve this using `--disable-warnings-as-errors` option, but it didn't work.
- [X] **Configure**: ```./configure --with-toolchain-version=2022```
- [X] **Build**: ```make images```

## Using WSL
If I remember correctly that only the `JetBrains Runtime` build was successful on WSL, and failed with other distributions.

I tried this again while writing this document, but I couldn't build it. I'll try again later.
