# About
Multiboot flash drive creation

## Core statements
* Linux boots Linux
* no boring installs, just `cp my.iso /to/my/usb_drive/`
* do best for known distro images, try to boot random (even if they do not want to)

## Software involved
* [GNU sed](http://www.gnu.org/s/sed/)
* [NetbootCD](http://netbootcd.tuxfamily.org/)
* [Syslinux](http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project)
* [Tiny Core Linux](http://distro.ibiblio.org/tinycorelinux/)

## Boot process
* Syslinux, or another bootloader, boots the NetbootCD image
* User scramble through dialogs, and select an image to boot
* kexec loads the kernel from the selected image, using _improved_ initrd with _improved_ cmdline
* mbd takes control before the initrd /init, and performs distro specific preparations
* initrd /init prepare root filesystem
* mbd take control again, before filesystem switch, and performs some special tasks
* /init continue boot

# Usage
## Get
Run next commands:

    git clone git://github.com/b3b/mbd.git
    cd mbd

## Configure
Run
    
    autoconf
Run _configure_ with the _target_device_ environment variable set to partition device file. If /dev/_PARTITION_ is your USB flash drive partition device file (as "sdx1", or "disk/by-uuid/NNNN"), run
    
    ./configure target_device=/dev/PARTITION

### Additional options
* isolinux\_dir="DIR" - install to _DIR_ directory on USB flash drive. _DIR_ is "isolinux" by default
* --without-bootloader - do not install Syslinux bootloader on the device. Use this option to preserve existent bootloader. Need this option if target filesystem is not FAT32
* mbd\_label="LABEL" - set filesystem label to _LABEL_, "MBOOTDISK" by default

If _without-bootloader_ option is used, it is necessary to set target filesystem label to be the same as _mbd\_label_ value. Label can be set with the mlabel command (for FAT32), e2label command (for ext2/ext3/ext4).

## Build
On build stage, script will download NetbootCD and Tiny Core Linux live CDs; download and build GNU sedstream editor. Run

    make

## Install
Need root privileges. If option _without-bootloader_ is not set, script will install bootloader (Syslinux) on target device. Run

    make install

## Use
Put LIVE CDs (*.iso) into the images directory ("isolinux/iso" by default) on your USB flash drive. Example, if MP is flash USB drive mount point:

    cp my-cool-live-cds/*.iso MP/isolinux/iso/
    mkdir MP/isolinux/iso/Debian
    cp my-cool-live-debian-cds/*.iso MP/isolinux/iso/Debian/

Boot from USB flash drive, and follow the menus

## Uninstall
From mbd source directory, run

    make uninstall

# Special Use
Add desktop link to Live CD desktop. Run configure with the _desktop_link_ environment variable set. Example:

    ./configure target_device=/dev/PARTITION desktop_link='http://xn--c1apc3a.xn--p1ai/'

Boot Live CD from running system. Example, if MP is flash USB drive mount point:

    cd MP/isoinux
    mkdir /tmp/mbd
    sh mbd_menu -t /tmp/mbd

# Tested with
<table>
<tr>
<tr><th>Distribution</th><th>Status</th></tr>
<tr><td><a href="http://live.debian.net/">Debian Live</a></td><td>work</td></tr>
<tr><td><a href="http://fedoraproject.org/wiki/FedoraLiveCD">FedoraLiveCD</a></td><td>work</td></tr>
<tr><td><a href="http://grml.org/download/">Grml</a></td><td>work</td></tr>
<tr><td><a href="http://www.linuxmint.com/download.php">Linux Mint CD</a></td><td>work</td></tr>
<tr><td><a href="http://www.sabayon.org/mirrors">Sabayon Linux</a></td><td>work</td></tr>
<tr><td><a href="http://www.slitaz.org/en/get/index.html#stable">SliTaz LiveCD</a></td><td>work</td></tr>
<tr><td><a href="https://tails.boum.org/download/index.en.html">Tails</a></td><td>work</td></tr>
<tr><td><a href="http://distro.ibiblio.org/tinycorelinux/downloads.html">Tiny Core Linux</a></td><td>work</td></tr>
<tr><td><a href="http://www.ubuntu.com/download/ubuntu/download">Ubuntu</a></td><td>work</td></tr>
<tr></tr>
<tr><td><a href="http://www.damnsmalllinux.org/">Damn Small Linux</a></td><td><b>not</b> work</td></tr>
<tr><td><a href="http://www.slax.org/get_slax.php">Slax</a></td><td><b>not </b>work</td></tr>
</table>
