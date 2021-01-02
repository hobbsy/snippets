# How to install snap programmes on WSL2 Ubuntu 20.04 LTS

To install and run [snap](https://snapcraft.io/install/get-iplayer/ubuntu) programmes on Ubuntu 20.04.1 LTS under WSL2 on Windows 10 x86_64 (eg. for programmes like [get-iplayer](https://github.com/get-iplayer/get_iplayer)) I used the following code by sunliusi found [here](https://github.com/microsoft/WSL/issues/5126#issuecomment-653715201) to get snap up and running:




```
sudo apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig
sudo daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target
exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME
```

I was then able to install get-iplayer on WSL2 Ubuntu using

```
sudo snap install get-iplayer
```

Futher reading:

https://discourse.ubuntu.com/t/using-snapd-in-wsl2/12113

https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033

https://github.com/DamionGans/ubuntu-wsl2-systemd-script

https://www.youtube.com/watch?v=cWlYe0CE2iU&feature=youtu.be
