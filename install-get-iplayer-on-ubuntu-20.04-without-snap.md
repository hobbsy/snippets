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
(this will make sure you have all the dependencies and programmes required in place already)

`` sudo apt install libwww-perl liblwp-protocol-https-perl libmojolicious-perl libxml-libxml-perl libcgi-pm-perl ``

`` sudo apt install build-essential cpanminus liblocal-lib-perl ``

`` sudo apt install atomicparsley ffmpeg ``


then I made a sub-directory for get-iplayer under my home directory
~/Code/get-iplayer
(this bit isn't necessary)

`` cd ~ ``
`` mkdir Code/get_iplayer ``
`` cd Code/get_iplayer ``

Download the latest get_iplayer CLI release to working directory

`` wget https://raw.githubusercontent.com/get-iplayer/get_iplayer/master/get_iplayer ``

Install get_iplayer CLI script


`` sudo install -m 755 ./get_iplayer /usr/local/bin ``

The notes say "If /usr/local/bin is not in $PATH, use another location appropriate for your system, e.g., /usr/bin."

You can check what locations are in your PATH by running the command

`` $PATH ``



Now you should be able to use get-iplayer from the command line using

``  get_iplayer  ``

If you need help with basic commands you can refer to:  
https://github.com/get-iplayer/get_iplayer/wiki/tutorials  
https://www.squarepenguin.co.uk/guides/  

or via the command line:

` get_iplayer --help `  
` get_iplayer --basic-help`  
` get_iplayer --long-help`  
` man get_iplayer`  

or

https://github.com/get-iplayer/get_iplayer/wiki/manpage  
https://github.com/get-iplayer/get_iplayer/wiki/options  
https://github.com/get-iplayer/get_iplayer/wiki/webpvr  
https://github.com/get-iplayer/get_iplayer/wiki/faq  
https://github.com/get-iplayer/get_iplayer/wiki/search  




a good starting command to search everything available on iPlayer TV and Radio is

`` get_iplayer --type=tv,radio ".*" ``



references:
https://github.com/get-iplayer/get_iplayer/wiki/installation  
https://github.com/get-iplayer/get_iplayer/wiki/unix   
