#  TrueNAS Scale Installation

!!! warning "Warning"
    This guide was written for version **24.04.1.1** of TrueNAS SCALE and has been performed on a virtual machine.

## ISO Preparation

Download the operating system image from the official website. It is recommended to verify the integrity of the downloaded image using the files provided by the site with PGP or SHA256.

Once the image has been verified, it should be written to a flash memory drive to provide it to the target system. This can be done using `dd` on Linux:

```
dd bs=4M if=[ISO PATH] of=/dev/[FLASH MEMORY PATH] conv=fsync oflag=direct status=progress
```

## Installation

Insert the flash memory into the target PC and boot from it using the boot menu (usually accessible by pressing F11 during the boot sequence). Note that *secure boot* must be disabled to install TrueNAS.

At boot, a selection screen will appear; simply wait 5 seconds and the first option will be chosen automatically.

![](../boot.png)

On the first menu shown after the boot sequence, select *Install/Upgrade*.

![](../install-upgrade.png)

Choose the disk on which to install the operating system. It is advisable to use **two** boot disks to ensure that the system remains operational even if one of the disks fails. In my case, I will select the virtual disk `/dev/sdb`.

![](../drive.png)

Confirm the selection and choose the third option to configure the *admin* user from the Web interface.

![](../admin.png)


After the installation is complete, reboot the system and, in the BIOS configuration, select the disk on which TrueNAS was installed as the primary boot disk.