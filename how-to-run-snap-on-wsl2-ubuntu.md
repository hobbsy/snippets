## How to install snap programmes on WSL2 Ubuntu 20.04 LTS

**IMPORTANT: Do not blindly follow these instructions below as they didn't work out for me**

Read through the whole page before typing in any commands, I am not responsible for this breaking your system (as it did for me)

**My Notes**

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

edit - although it worked once, when you close down your WSL2 window it seems to give an error next time you run WSL2:

typing:

````
get-iplayer
````

displays the error

```
internal error, please report: running "get-iplayer" failed: cannot find installed snap "get-iplayer" at revision 250: missing file /snap/get-iplayer/250/meta/snap.yaml
```

I then tried following this [old forum post on snapcraft](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)

although it appears the most up to date code has now been moved to a [Github script](https://github.com/DamionGans/ubuntu-wsl2-systemd-script)

I did have get-iplayer up and running initially but it stopped after closing and re-opening WSL2.
Having followed the instructions on snapcraft and run the Github script I now see when typing 'get-iplayer'

```
internal error, please report: running "get-iplayer" failed: cannot find installed snap "get-iplayer" at revision 250: missing file /snap/get-iplayer/250/meta/snap.yaml
```

I tried removing and re-installing it:

```
thinkpad@X1C6:~$ sudo snap remove get-iplayer
get-iplayer removed
thinkpad@X1C6:~$ sudo snap install get-iplayer
get-iplayer 3.26 from Snapcrafters installed
```
but now when I run 'get-iplayer' I see the error:

```
cannot perform operation: mount --rbind /dev /tmp/snap.rootfs_l9mHp2//dev: No such file or directory
```

at this point I am stuck... please drop me a Tweet @hobbsy if you can help :)


to disable the script I tried editing bash.bashrc to comment out (add a # at start of line)

```
nano /etc/bash.bashrc
```

```
# Start or enter a PID namespace in WSL2
source /usr/sbin/start-systemd-namespace
```
add a # in front of line starting source

eg.

```
# Start or enter a PID namespace in WSL2
# source /usr/sbin/start-systemd-namespace
```

I have a feeling I may have not have properly followed the instructions for installing get_iplayer as a snap.

See the [Unix install notes on the get-iplayer Github](https://github.com/get-iplayer/get_iplayer/wiki/unixpkg) and scroll down past the section **Distros with snap support**

```
IMPORTANT: The default get_iplayer profile directory will be $HOME/snap/get-iplayer/common/.get_iplayer rather than $HOME/.get_iplayer ($HOME is set to the value of $SNAP_USER_COMMON in the snap environment). Immediately after upgrading from a PPA version to the snap version, you must move or copy the contents of your profile directory to the location used by the snap version:

code starts:

 # run once to ensure snap version initialises profile directory
  get_iplayer
  # move/copy contents of profile directory
  mv ~/.get_iplayer/* ~/snap/get-iplayer/common/.get_iplayer
  # OR
  cp -r ~/.get_iplayer/* ~/snap/get-iplayer/common/.get_iplayer

code ends
 

If an "ERROR: Cannot read options file: /etc/get_iplayer/options" message appears when you run the snap version, remove the indicated directory (it is not required by get_iplayer):

  sudo rm -fr /etc/get_iplayer

get_iplayer will not be able to create files on removable devices mounted under /media, /run/media or /mnt unless the snap's "removable-media" interface is connected:

  sudo snap connect get-iplayer:removable-media

You can also select "Read/write files on removable storage devices" in the permissions for get-iplayer in the Ubuntu Software/Snap Store desktop application (if available) after installation. If your removable device is mounted in another location, you may be able to use a bind mount to access it somewhere under your home directory.

``` 
actually that might not be relevant as I am not upgrading from a PPA install to a snap install...


**Futher reading/bookmarks:**

https://discourse.ubuntu.com/t/using-snapd-in-wsl2/12113

https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033

https://github.com/DamionGans/ubuntu-wsl2-systemd-script
https://github.com/diddledan/ubuntu-wsl2-systemd-script

https://www.youtube.com/watch?v=cWlYe0CE2iU&feature=youtu.be

https://gitlab.com/relief-melone/wsl-initial-setup

https://snapcraft.ninja/2020/08/06/starting-systemd-in-wsl-when-you-login-to-windows-youll-be-astounded-by-the-speed-improvement/

https://github.com/arkane-systems/genie

https://github.com/microsoft/WSL/issues/994
https://github.com/microsoft/WSL/issues/5126


