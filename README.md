# Netgear R6220-100INS AC1200 OpenWrt Firmware

This is a modified ramips build for the netgear R6220-100INS.

**Factory partition adjusted**, verify WAN interface MAC address with that printed on packaging.

The package selection and configuration was intended for personal/home use and is overall lighter. This build includes LuCi interface with some useful luci-applications such as adblock, printer-server, samba, mwan3, sqm, etc.
**Change branch for base builds.**

**[Note: This model of R6220 is the 100INS which is currently being sold on Amazon India, please verify the model name printed on the packaging before proceeding with installation]**

Install Instructions:
  1. Enable debug mode: ```http://<router_ip>/setup.cgi?todo=debug   [usually 192.168.1.1]```
  2. Copy squashfs-rootfs.bin and squashfs-kernel.bin to a USB drive
  3. Telnet <router_ip> and login as root
  4. Connect the USB drive
  5. Check whether USB drive is recognised ``` ls /mnt/shares```
  6. Enter the USB drive ``` cd /mnt/shares/<usb drive>```
  7. Install the binaries and reboot
  ``` 
  mtd_write write <***squashfs-rootfs.bin> Rootfs
  mtd_write write <***squashfs-kernel.bin> Kernel
  reboot
  ```
  
Update Instructions:
1. Through OpenWrt web interface ```Luci > System > Upgrade > ***-sysupgrade.tar```
2. Through OpenWrt CLI
```
scp ***-sysupgrade.tar root@<router_ip>:/tmp/
ssh root@<router_ip>
sysupgrade -v /tmp/***-sysupgrade.tar
```

Brick Recovery:
1. If something goes south, use [nmrpflash](https://github.com/jclehner/nmrpflash) for brick recovery.
2. Obtain router default firmware from [Netgear Support](https://www.netgear.com/support/product/R6220#download).




*The builds will be updated every month/on-request. Request support for customised builds. If you're having trouble, create an issue on GitHub, or request for support [here](mailto:jayanta.gogoi525@gmail.com)*
