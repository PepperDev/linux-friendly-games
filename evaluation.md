# Evaluation Guide

As mentioned in the [readme](README.md), here it's elaborated the evaluation criteria. Each criterea worth at most one point, its sum is the game's final rank.

The list must be presented in rank order first, then untied by name. Games that are not playable on Linux should not even be mentioned.

### anticheat free

It's pretty streight forward, if the game is listed at [AreWeAntiCheatYet](https://github.com/AreWeAntiCheatYet/AreWeAntiCheatYet), even if it works smoothly on Linux, it worths zero points at anticheat free.

### native linux binary

If the game does not provided any [ELF](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format) binary, or if the source code is provided but it's not possible to generate a valid ELF from it without code change, it worth zero points in this category.

If the game provide the source code, even if it does not provide all binaries, consider the possiblility to generate the ELF from source for the missing machine architectures, if it works it worth the same as if the game provides such binaries.

For the evalution please consider at least the following machines: x86 (i386), amd64 (x86\_64), arm (armhf/armv7), aarch64 (arm64). In sequence: 0x03, 0x3E, 0x28, 0xB7.

* if the game provides binaries for all the mentioned machines it worth one full point;
* if it provides for amd64 and at least one more it worth 0.9;
* if it provides only for amd64 it worth 0.8;
* if it provides only for x86 or for more than one but not including amd64 it worth 0.7;
* if it provides only for one not including amd64 nor x86 it worth 0.6;

### wayland

Some games use engines or libraries, such as [SDL](https://wiki.libsdl.org/SDL2/FAQUsingSDL), that may support Wayland natively without XWayland with little to no effort. If declaring an environment variable is all it needs to work on Wayland the game worth one full point in this regard.

If it requires complex configuration or mild code change in case the source is provided, then it worth 0.5 points.

### libc

If the game provides the source code and it's possible to build it for any libc it worth one full point.

If the game provides a dynamic built binary but a simple symbolic link to it's interpreter (that can be retrieved by `readelf -l /path/to/binary | grep interpreter` or `patchelf --print-interpreter /path/to/binary`), or changing it with `patchelf --set-interpreter /lib/path-to-libc.so /path/to/game-binary`, is enough to make it work then it worth 0.9 points. If the game provides its own dynamic libraries the same proccess must apply for all.

If the game provides a statically built binary, with no dynamic library dependency not even the libc, it worth 0.8 points.

If the game requies some glibc specific symbols which are provided by gcompat package, making it possible to run on other libc, thus it worth 0.5 points.

### open source

If the game provides the source code with all it's dependencies, libraries and all content, free for building and use, then it worth one full point.

If the game provides the source code but limit it's content or depend on closed source components or libraries, then it worth 0.5 points.

### maintenance

It's not only content, the libraries the games depends on are eventually updated to fix vulnerabilites and such it the game maintainer's duty to keep it up to dated, regardless if it's open source or not.

* if the last update was made at most six months ago it worth one full point.
* if the last update was between six months and two years it worth 0.8 points.
* if the last update was between two and five years it worth 0.5 points.

## Category

The category should be one of the following list:

* Board
* Card
* FPS
* MMORPG
* Simulator
* TPS

If more than one category could fit please choose the one most relevant for the game, if no category fits please open a [discussion](discussion/new) for possible inclusion.

## Including a new game

If all tests are corrently performed the game can be included by opening a new [pull request](pr/new) and following its template.
