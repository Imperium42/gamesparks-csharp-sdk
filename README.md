## Community Edition

* This fork is the primary community fork to ensure pull requests go through. Collaborate with us @ https://discord.gg/wSD7huJ #gs-general
* At the time of writing this, the parent fork had 2 commits. If this goes higher, let's remind each other to pull.

## Using Src Directly?
Using src code directly (opposed to DLLs) can allow you to easily edit src and step-through via Visual Studio. If you want to swap your GS project from DLLs to src:

1. Backup (Git?)
2. CLOSE Unity (dll's persist while open)
3. Find your /GameSparks dir, and DELETE following files
```
/GameSparks
  ./Plugins
    ./GameSparks.Api.dll
    ./GameSparks.dll
    ./GameSparksRT.dll
```
4. Create dir `./src`
5. Drop everything from `/gs-csharp-community-sdk/Projects/` to the new `src` dir
6. Open `/src/bccrypto-csharp-1.8.1/crypto/src` -> Rename `AssemblyInfo.cs` to `AssemblyInfo.cs.bak` (it's a dupe).
7. Open `/src/Properties` -> Rename `AssemblyInfo.cs` to `AssemblyInfo.cs.bak` (it's a dupe).
8. Apply the [latest WebSocket patch](https://github.com/Imperium42/gs-csharp-community-sdk/issues/6)
9. Open Unity >> Refresh (CTRL+R), if necessary. 

✅ You're using native C# src! You can now utilize step-thru debugging with GS src.

## TODO:
1. Full release instead of src+patch ([$500 AWS credits bounty](https://github.com/Imperium42/gs-csharp-community-sdk/issues/6) for pull request!)

________________________

## Gamesparks Unity Sources

This repository contains the sources for the binaries included with the GameSparks Unity SDK.

Each project build the release assets to /Projects/GameSparksUnity/* (this is the folder structure that required in unity)

## C# projects

Contained within gamesparks-unity-sources.sln

### Projects/bccrypto-csharp-1.8.1/crypto/BouncyCastle_GameSparks.csproj

BouncyCastle assembly with a reduced class set to minimise the final asembly size.

This project builds the assembly for all supported platforms.

### Projects/GameSparks/GameSparks.csproj

Source for GameSparks.dll. This project builds the assembly for all supported platforms excluding the following:

Windows Metro
Windows UWP
Windows Phone 8


### Projects/GameSparks.Api/GameSparks.Api.csproj

Source for GameSparks.Api.dll This project builds the assembly for all supported platforms.

### Projects/GameSparks.Realtime/GameSparksRT/GameSparksRT.csproj

Source for GameSparksRT.dll  This project builds the assembly for all supported platforms excluding the following:

Windows Metro

## License

This library is licensed under the Apache 2.0 License. 


## C++ projects

Contained within Projects/GameSparks.Native/build/GameSparksNative/GameSparksNative.sln

### Projects/GameSparks.Native/build/GameSparksNative/GameSparksNative.PS4.vcxproj

Native library for PS4. If "mbed_tls_net_ps4.inc" is reported missing, you need to request this file from gamesparks support.

### Projects/GameSparks.Native/build/GameSparksNative/GameSparksNative.Switch.vcxproj

Native library for Nintendo Switch

### Projects/GameSparks.Native/build/GameSparksNative/GameSparksNative.Win64.vcxproj

Native library for Win64

### Projects/GameSparks.Native/build/GameSparksNative/GameSparksNative.XBoxOne.vcxproj

Native library for XboxOne
