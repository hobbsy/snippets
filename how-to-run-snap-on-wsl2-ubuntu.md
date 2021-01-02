To install and run snap programmes on Ubuntu under WSL2 on Windows 10 (eg. for programmes like get-iplayer) I used the following code found here:

https://github.com/Microsoft/WSL/issues/2374

```
sudo apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig
sudo daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target
exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME
```
