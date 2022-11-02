# Ubuntu Desktop setup

After going through the `bootable Ubuntu Desktop` from a USB stick

I got this error:

```
$ sudo apt install build-essential
“No Installation Candidate” when trying to install build-essential
```

Ran:

```
$ sudo apt update
$ sudo apt install build-essential
```

# NetworkManager setup

[SO Answer](https://askubuntu.com/a/496545/324695)

[settings docs](https://developer.gnome.org/NetworkManager/0.9/ref-settings.html)

[example configurations docs](https://wiki.debian.org/NetworkConfiguration#DNS_configuration_for_NetworkManager)

[how to reload](https://wiki.gnome.org/Projects/NetworkManager/SystemSettings#Reloading_configuration)

# re-install cuda drivers

```
aaronlelevier@bwldr:~$  uname -m && cat /etc/*release
x86_64
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

aaronlelevier@bwldr:~$ uname -r
4.15.0-44-generic
```

# how to copy files from a Linux hard drive to a usb

Insert USB

Find the drive name, by running one of these comands:

```
lsblk
sudo fdisk -l
```

Make a directory

```
sudo mkdir /media/usb
```

Mount:

```
sudo mount /dev/sda /media/usb
```

Copy intended files from hard drive to usb

```
sudo cp -r ~/data /media/usb/data
```

Un-mount

```
sudo umount /media/usb
```

Eject

```
sudo eject /dev/sda
```

## References

[SO answer about power off vs. eject](https://unix.stackexchange.com/questions/178638/eject-safely-remove-vs-umount)

[SO answer mount and umount](https://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal)
