## rtl8188eus v5.3.9
## THIS MAY NOT WORK IN VIRTUAL BOX ,USE VMware
# Realtek rtl8188eus &amp; rtl8188eu &amp; rtl8188etv WiFi drivers

[![Monitor mode](https://img.shields.io/badge/monitor%20mode-supported-brightgreen.svg)](#)
[![Frame Injection](https://img.shields.io/badge/frame%20injection-supported-brightgreen.svg)](#)
[![MESH Mode](https://img.shields.io/badge/mesh%20mode-supported-brightgreen.svg)](#)
[![GitHub issues](https://img.shields.io/github/issues/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/issues)
[![GitHub forks](https://img.shields.io/github/forks/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/network)
[![GitHub stars](https://img.shields.io/github/stars/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/stargazers)
[![GitHub license](https://img.shields.io/github/license/aircrack-ng/rtl8812au.svg)](https://github.com/aircrack-ng/rtl8188eus/blob/master/LICENSE)<br>
[![Android](https://img.shields.io/badge/android%20(8)-supported-brightgreen.svg)](#)
[![aircrack-ng](https://img.shields.io/badge/aircrack--ng-supported-blue.svg)](#)


# Supports
* Android 7
* MESH Support
* Monitor mode
* Frame injection
* Up to kernel v5.8+
... And a bunch of various wifi chipsets


first update & upgrade
sudo apt-get dist-upgrade
# reade it.......
At first, open up your terminal and change it to root terminal.
Then first of all make an update using, “sudo apt update” command to update all of the packages of your kali Linux machine.
Then type, “sudo apt install dkms bc” command. We need this package for compiling the new driver for the Kali Linux machine and the TP-link adapter.
Now we need to install the header files. So, type “sudo apt install linux-headers-$(uname -r)” and then enter. Then it will install all the header files.
So, we need to blacklist all the drivers now. So, type, echo “blacklist 8188eu” >> “/etc/modprobe.d/Realtek.conf” and then enter.
Then again type the same command but this time type r8188eu instead of 8188eu. Then hit enter.
Now we need to remove the old module. So, type “rmod r8188eu.ko” .
Now you have to reboot your terminal machine. So, type “sudo reboot”.

# Howto build/install
1. You will need to blacklist another driver in order to use this one.
2. `echo "blacklist r8188eu" >> "/etc/modprobe.d/realtek.conf"`
3. `make && make install`
4. Reboot in order to blacklist and load the new driver/module.

# MONITOR MODE howto
Use these steps to enter monitor mode.
```
$ sudo airmon-ng check kill
$ sudo ip link set <interface> down
$ sudo iw dev <interface> set type monitor
```
Frame injection test may be performed with
(after kernel v5.2 scanning is slow, run a scan or simply an airodump-ng first!)
```
$ aireplay -9 <interface>
```

# NetworkManager configuration
Add these lines below to "NetworkManager.conf" and ADD YOUR ADAPTER MAC below [keyfile]
This will make the Network-Manager ignore the device, and therefore don't cause problems.
```
[device]
wifi.scan-rand-mac-address=no

[ifupdown]
managed=false

[connection]
wifi.powersave=0

[main]
plugins=keyfile

[keyfile]
unmanaged-devices=mac:A7:A7:A7:A7:A7
```

# Credits
Realtek       - https://www.realtek.com<br>
Alfa Networks - https://www.alfa.com.tw<br>
aircrack-ng.  - https://www.aircrack-ng.org<br>
<br>
And all those who may be using or contributing to it of anykind. Thanks!<br>
