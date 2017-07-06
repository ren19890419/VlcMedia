# VlcMedia

Unreal Engine 4 Media Framework plug-in using the Video LAN Codec (libvlc).


## About

This plug-in is still under development and likely has a lot of remaining issues
to be fixed. Use in production is not yet recommended.

Make sure to pull the *Tag* that matches your Unreal Engine version. If you sync
to *Master* the code may not compile, because it may depend on Engine changes
that are not yet available in the UE4 Master branch.


## Supported Platforms

This plug-in was last built against **Unreal Engine 4.17** and tested
against the following platforms:

- ~~Linux~~
- ~~Mac~~
- Windows

**IMPORTANT**: Please note that this repository contains pre-compiled binaries
for libvlc and its plug-ins, which are licensed under LGPL. This means that you
cannot create monolithic builds of your game without violating LGPL, the UE4
EULA or both. The libvlc libraries must remain dynamic libraries that are bound
at run-time - static linking is not allowed - and the licensing related files in
*/ThirdParty/vlc* must be retained.

This also means that this plug-in cannot work on platforms that do not support
dynamically linked libraries (i.e. iOS, HTML5) or do not currently implement
support for it (i.e. Android, XboxOne).

Epic is in the process of adding plug-in support to monolithic builds, but there
is no ETA yet. Once this is supported, you will be able to distribute monolithic
game and server builds with VlcMedia, provided that the libvlc libraries and
plug-ins remain as separate DLLs.


## Prerequisites

A relatively recent version of libvlc is required. The latest stable release
(currently 2.2.1) is not sufficient.

For Mac and Windows, the following nightly builds are currently included:
* Mac: vlc-3.0.0-20170608-0445-git.dmg
* Win32: vlc-3.0.0-20170608-0258-git-win32.zip
* Win64: vlc-3.0.0-20170608-0453-git-win64.zip

Nightly builds can be downloaded from the VideoLAN web site (see below).

For debugging on Win32 and Win64, you can download debug builds and replace the
corresponding files and folders in the *VlcMedia/ThirdParty/vlc/* directory.

### Linux

A suitable version of **libvlc** must be installed or compiled from source. If
you ship your game on Linux, you will likely want to include libvlc with it, so
that users don't have to install it themselves. We will eventually include those
binaries in this repository, although it is not clear what distros should be
supported and where the builds are coming from. A better workflow needs to be
established for this.

Once the VLC libraries are installed on your machine, you need to add their path
to your LD_LIBRARY_PATH](https://github.com/ue4plugins/VlcMedia/issues/17)
environment variable. Copying the libraries and VLC plug-in's into VlcMedia's
*/ThirdPart/vlc/Linux* directory is currently not supported out of the box as
the [Build.cs](https://github.com/ue4plugins/VlcMedia/blob/master/Source/VlcMedia/VlcMedia.Build.cs#L52)
file expects these files to be under the correct sub-directory for the target
architecture.

### Mac, Windows

All required libraries and plug-ins are included in the *ThirdParty* directory
and work out of the box.


## Dependencies

This plug-in requires Visual Studio and either a C++ code project or the full
Unreal Engine 4 source code from GitHub. If you are new to programming in UE4,
please see the official [Programming Guide](https://docs.unrealengine.com/latest/INT/Programming/index.html)! 


## Usage

You can use this plug-in as a project plug-in, or an Engine plug-in.

If you use it as a project plug-in, clone this repository into your project's
*/Plugins* directory and compile your game in Visual Studio. A C++ code project
is required for this to work.

If you use it as an Engine plug-in, clone this repository into the
*/Engine/Plugins/Media* directory and compile your game. Full Unreal Engine 4
source code from GitHub is required for this.


## Support

Please [file an issue](https://github.com/ue4plugins/VlcMedia/issues), submit a
[pull request](https://github.com/ue4plugins/VlcMedia/pulls?q=is%3Aopen+is%3Apr)
or email us at info@headcrash.industries


## References

* [VideoLAN Homepage](http://videolan.org)
* [VideoLAN Nightly Builds](http://nightlies.videolan.org/)
* [Introduction to UE4 Plugins](https://wiki.unrealengine.com/An_Introduction_to_UE4_Plugins)
