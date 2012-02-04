# About
Multiboot flash drive creation

# Usage
## Get
Run next commands:
    git clone git://gitorious.org/multi-boot-disk-test/multi-boot-disk-test.git
    cd multi-boot-disk-test
## Configure
Run
    autoconf
Run _configure_ with the _target_device_  environment variable set to partition device file. If /dev/_PARTITION_ is your USB flash drive partition device file (as "sdx1", or "disk/by-uuid/NNNN"), run
    ./configure target_device=/dev/PARTITION
## Build
On build stage, script will download [NetbootCD](http://netbootcd.tuxfamily.org/) and [Tiny Core Linux](http://distro.ibiblio.org/tinycorelinux/
) live CDs; download and build [GNU sed stream editor](http://www.gnu.org/s/sed/). Run
    make
## Install
Need root privileges. Script will ask for confirmation, before boot loader ([Syslinux](http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project)) install. Run
    make install
## Use
Put LIVE CDs (*.iso) images into the "isolinux/iso" directory on your USB flash drive. Example, if MP is flash USB drive mount point:
    cp my-cool-live-cds/*.iso MP/isolinux/iso/
    mkdir MP/isolinux/iso/Debian
    cp my-cool-live-debian-cds/*.iso MP/isolinux/iso/Debian/
Boot from USB flash drive, and follow the menus
## Uninstall
From mbd source directory, run
    make uninstall

# Special Use
Add desktop link to Live CD desktop. Run configure with the _desktop_link_ environment variable set. Example:
    ./configure target_device=/dev/PARTITION desktop_link='http://www.gitorious.org'
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

