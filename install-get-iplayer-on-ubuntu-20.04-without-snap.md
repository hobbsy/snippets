## How to install get-iplayer on Ubuntu 20.04.2 without using snaps

The easiest way to install get-iplayer on the latest Ubuntu install seems to be using snaps


`` sudo snap install get-iplayer ``

source:
https://snapcraft.io/get-iplayer
https://snapcraft.io/install/get-iplayer/ubuntu


However - if you want to avoid using snap, you can do a manual install

Here are some notes....

source:
https://github.com/get-iplayer/get_iplayer/wiki/unix

summary of commands for Ubuntu 20.04.2

`` sudo apt install libwww-perl liblwp-protocol-https-perl libmojolicious-perl libxml-libxml-perl libcgi-pm-perl ``

`` sudo apt install build-essential cpanminus liblocal-lib-perl ``

`` sudo apt install atomicparsley ffmpeg ``

