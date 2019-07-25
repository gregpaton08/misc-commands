# Miscellaneous Commands
Various commands that I find myself searching for far too often.

## Redirect stdout and stderr to File
```
command >output.txt 2>&1
```

## Create a USB Installer for a Linux Distro
```
diskutil list # to find the target USB drive
diskutil unmountDisk /dev/diskN
sudo gdd if=Downloads/debian-live-10.0.0-amd64-gnome.iso of=/dev/diskN bs=1M status=progress
```

## Check all open ports on a host
```
sudo nmap -v -sT <host_name>
```

## Scan all IP Addresses on the Network in a Range
```
# wildcard
sudo nmap -sn 10.1.2.*
 
#range
sudo nmap -sn 10.1.2.0-128
```

## Run a script in the background

Allows you to ssh into a server, run a script in the background, and exit.
```
nohup <your command here> &
```

To kill the command find the process ID with
```
ps -ef | grep <some search term>
```

and kill the command with
```
sudo kill -9 <pid>
```

## Install Debian on Lenovo x120e
For lack of a better place to note this...

1. Boot into recovery mode.
2. Find the name of the network interface with `ip link show`.
3. Run `dhclient enp1s0` to get the ethernet working.
4. Update the sources in `/etc/apt/sources.list`.
    ```
    deb http://ftp.us.debian.org/debian/ testing main non-free contrib
    deb-src http://ftp.us.debian.org/debian/ testing main non-free contrib
    ```
5. Update and upgrade and install some firmware.
    ```
    apt-get update -y
    apt-get upgrade -y
    apt-get install firmware-amd-graphics
    ```
