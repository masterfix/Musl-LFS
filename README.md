# Musl-LFS
Linux From Scratch using Musl as Libc and S6+S6-rc as init system

This is based on the works of Linux From Scratch (http://www.linuxfromscratch.org), which use GLibc and SysVinit/systemD. Additional work was derived from Void Linux (https://voidlinux.org), Alpine Linux (https://alpinelinux.org), and Dragora Linux (https://dragora.org). For logging during development of tool chains, I used porg from http://porg.sourceforge.net/.

The aim of this project is to create a create a Linux system using Musl (www.musl-libc.org) instead of GNU's Glibc and S6 (https://skarnet.org/) instead SysVinit.

## Supported Architectures
<ul>
  <li>i686/i586 : Stable and tested. Stable enough to build Xorg, Qt5 (without QT-webengine), Rust, and Firefox.</li>
  <li>x86_64 : Stable and tested. Stable enough to build Xorg, Qt5, Rust, and Firefox.</li>
  <li>aarch64: Stable and tested. Stable enough to build Xorg, Qt5, Rust, and Firefox.</li>
  <li>armv7/armv6: Builds fine. Requires modification to suit target hardware.</li>
</ul>

## Goals:
<ul>
  <li> [x] Properly name patches to reflect origin (i.e. Alpine or void) </li>
  <li> [ ] Create a list for wget to download sources.</li>
  <li> [ ] Create md5s list for sources</li>
  <li> [ ] Update s6-rc & s6 to lastest version </li>
  <li> [x] Redesign tool chain build to avoid two build passes of binutils and GCC</li>
  <li> [ ] Generate HTML 'book' like LFS</li>
  <li> [ ] Add utmp/utmpx implementation</li>
  <li> [ ] Transition from pkgconfig to pkgconf</li>
  <li> [ ] Transition from gettext to gettext-tiny?</li>
  <li> [ ] POSIX compatibility </li>
</ul>

## Tested Builds

| Host         | Target      | Build Status   |
| ------------ | ----------- | -------------- | 
| i686-musl    | i686-musl   | Pass |
| i686-glibc   | i686-musl   | Pending |
| x86_64-musl  | x86_64-musl | Pass |
| x86_64-glibc | x86_64-musl | Pass |
| aarch64-glibc | aarch64-musl | Pass |
| armv7l-glibc | armv7l-musl | Pass |
| armv7l-musl  | armv7l-musl | Pending |
| armv6-glibc  | armv6-musl  | Pending |
| armv6-musl   | armv6-musl  | Pending |

*ARM builds will need some modification based on specific hardware*

## Additional Required Packages 

If pursuing BLFS, some packages will fail to compile due certain implementions left out in the Musl C Library.

<ul>
<li>Musl C Library
https://www.musl-libc.org/</li>

<li>Musl-FTS 
https://github.com/pullmoll/musl-fts</li>

<li>Musl-Obstack
https://github.com/pullmoll/musl-obstack</li>

<li>Musl-RPmatch
https://github.com/pullmoll/musl-rpmatch</li>

<li>Musl-Legacy-Compatibility Headers
https://github.com/void-linux/void-packages/blob/master/srcpkgs/musl-legacy-compat </li>

<li>Argp-Standalone
https://github.com/jahrome/argp-standalone</li>

</ul>

## Optional Packages:
<ul>
<li>LibreSSL (instead of OpenSSL)
https://www.libressl.org/</li>
<li>GNU Nano (Text Editor)
https://www.nano-editor.org/ </li>
</ul>

## Projects of Interest

<ul>
<li>gCompat - "The gcompat project provides a glibc-compatible runtime environment for distributions that use musl libc."
https://code.foxkit.us/adelie/gcompat</li>
<li> Locales - "Locale program for musl libc"
https://github.com/rilian-la-te/musl-locales </li>
<li>Mussel - "...the shortest and fastest script available today to build working cross compilers that target musl libc."
https://github.com/firasuke/mussel </li>
<li>shimmy - POSIX:registered: compatibility shims for Linux (and other environments)
https://code.foxkit.us/adelie/shimmy</li>
<li>gettext-tiny - It provides lightweight replacements for tools typically used from the GNU gettext suite.
https://github.com/AdelieLinux/gettext-tiny</li>
</ul>

## Layout

<ul>
  <li>build-scripts - [WIP] Build scripts to use to semi-automate building /cross-tools, /tools, and the final system</li>
  <li>contrib - Additional sources that are hard to find or re-packed
  <li>doc - Build instructions to build a LFS installation that uses Musl instead of Glibc and S6 instead of SysVint.</li>
  <li>extra - Helpful scripts to mount, chroot, and umount a MLFS build.</li>
  <li>files - Files that will be needed during the build</li>
  <li>patches - All patches used to patch sources to work/recognize Musl C Library</li>
  <li>sources.list - List of sources to download
</ul>

## Changelog (since 6.00)

<ul>
 <li>Upgraded to GCC-10.2.0 and several other packages</li>
 <li>Added musl-rpmatch to build</li>
 <li>Add zstd to build</li>
 <li>Changed tool chain build flow to build binutils and GCC once</li>
 <li>Added nano text editor for tool chain - Helps with troubleshooting</li>
 <li>Updated patches and files directory scheme to reflect origins</li>
 <li>Removed porg. Recommend use of Slackware's pkgtools</li>
</ul>
