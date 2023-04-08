This patchset contains fixes for a working LLVM + Musl Gentoo installation.

They can be dropped at /etc/portage/patches.

# Similar repositories

Most issues are musl related and patches for them can be found at:

* [Chimera Linux source packages](https://github.com/chimera-linux/cports)
* [Void Linux source packages](https://github.com/void-linux/void-packages/tree/master/srcpkgs)
* [Alpine Linux ports tree](https://git.alpinelinux.org/aports/tree/)
* [OpenEmbedded recipes](https://git.openembedded.org/openembedded-core/tree/meta)

For the minority of strictly LLVM-related issues, fixes sometimes can be found at the [FreeBSD ports tree](https://cgit-dev.freebsd.org/ports/) or at [MacPorts](https://github.com/macports/macports-ports). Be aware that, as non-Linux operating systems, some of their patches might be irrelevant or even breaking on Linux.

# Contributing

Feel free to make a PR to add new patches or remove obsolete ones (either because the original developers fixed the issue, or because Gentoo maintainers added them to the Portage tree).

It is recommended to prefix your commit messages with `category/package: ` and credit your source. Examples:

```
net-fs/davfs2: add patches from void linux
media-gfx/gimp: fix return type for Clang 15 build
```
