## Copyright & License Notices

Original Work: Copyright (C) Ente — https://github.com/ente/ente  
Modifications: Copyright (C) 2026 Melvin Quick — Removal of bundled GPU/Display Libraries

This project is licensed under AGPL-3.0. See [LICENSE](./LICENSE).

> **Unofficial community fix.** This project is not affiliated with or endorsed by Ente. "Ensu" and "Ente" are trademarks of their respective owners.

## Purpose

To fix Ente's broken Ensu AppImage downloads.

## Problem

When trying to install Ente's Ensu AppImage on Arch Linux running Wayland, I noticed I am able to install; however, the application errors out unless run with an LD_PRELOAD of the libwayland-client.so.0 library, like so:

`LD_PRELOAD=/usr/lib/libwayland-client.so.0`

This command forces the AppImage to run using the host system libraries for display instead of the libraries baked into the AppImage.

## Resolution

If you extract their AppImage file and remove all of the baked in display libraries and build it again, then it runs with no problem as it defaults to using the host system libraries instead of the baked in libraries (which are no longer present).

## Process

The steps I'm taking to do this are the following:

1. Retrieve the latest Ensu AppImage from the [Ente GitHub Page](https://github.com/ente/ente).
2. Make the AppImage file executable to allow it to be extracted.
3. Extract it.
4. Remove the unnecessary display libraries that cause it to break when run without specifying to use the host libraries.
5. Repackage it using appimagetool.
6. Remove the squashfs-root folder from the extraction and rebuilding as cleanup.
7. Upload it as a new release in this repo.

## Useful Information

[Project](https://github.com/users/melvinquick/projects/15)  
[Latest Release](https://github.com/melvinquick/ente_ensu_appimage_fix/releases/latest)
