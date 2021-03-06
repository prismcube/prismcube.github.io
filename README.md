# Prismcube Ruby

![image](/files/Prismcube-Ruby_front-625x171.jpg)

# Introduction
Prismcube Ruby was made by the Korean manufacture Marusys which also makes the Vu+ receivers.

The Prismcube Ruby was sold in Europe by Ab-Com under the name AB IPBox Prismcube Ruby. In the Middle East the same receiver is sold under the name PRISMCUBE KASYS by KASYS International we have also seen an Openbox branded version.

The Prismcube was not an Enigma2 based receiver like most of the stb in the market. It is the first to come with XBMC. XBMC Media Center is an award-winning free and open source cross-platform software media player and entertainment hub for digital media. So the Prismcube is something new representing XBMC4STB an entirely new platform and it will be interesting to see if it can compete with Enigma2.

Prismcube Ruby was a satellite tv only receiver with twin fixed DVB-S2 tuners. The hardware is pretty basic which also is reflected in the price. We are not talking high end here.

Key Features on the Prismcube Ruby:  
  CPU: PNX8496-1250DMIPS  
  4Gb * 8bit (Only 512mb of Ram available)  
  Easy option to fit Internal SATA HDD 2.5  
  1 card reader (needs softcam software to be functional)  
  1 CI slot  
  Front display (12 Digit VFD)  
  Ethernet  
  WiFI built in  

(source https://linux-tv.com/receiver/ab-ipbox-prismcube-ruby/ for full review)

# Informations..

This is an attempt to allow to build images for this dead box again.

# How to build:

Prepare a vm with a quite old linux installation (a debian wheezy could be ok) 
..or install into chroot  

sudo debootstrap --arch=i386 --keyring=/usr/share/keyrings/debian-archive-removed-keys.gpg wheezy wheezy http://archive.debian.org/debian  
sudo mount -o bind /dev wheezy/dev  
sudo mount -o bind /dev/shm wheezy/shm  
sudo mount -o bind /dev/pts wheezy/pts  
sudo mount -o bind /proc wheezy/proc  
sudo mount -o bind /sys wheezy/sys  
sudo mkdir wheezy/prismcube  
sudo chroot wheezy
apt-get install build-essential git gawk python diffstat makeinfo chrpath  
DEBIAN_FRONTEND=noninteractive dpkg-reconfigure dash  

Download https://prismcube.github.io/files/Makefile

To build the development branch:
$ make BRANCH=angstrom-v2012.12-yocto1.3-dev  

To build the release branch (untested):
$ make  



