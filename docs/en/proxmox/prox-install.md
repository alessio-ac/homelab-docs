# Proxmox Installation

!!! warning "Warning"
    This guide was written for version **8.2** of Proxmox and has been performed on a virtual machine.

## ISO Preparation

Download the operating system image from the official website. It is recommended to verify the integrity of the downloaded image using the files provided by the site with PGP or SHA256.

Once the image has been verified, it should be written to a flash memory drive to provide it to the target system. This can be done using `dd` on Linux:

```
dd bs=4M if=[ISO PATH] of=/dev/[FLASH MEMORY PATH] conv=fsync oflag=direct status=progress
```

## Installation

Insert the flash memory into the target PC and boot from it using the boot menu (usually accessible by pressing F11 during the boot sequence).

At boot, a selection screen will appear; simply wait 5 seconds and the first option will be chosen automatically.

First, accept the EULA and select the disk where Proxmox will be installed. In my case, */dev/sda*.

![](../prox-drive.png)

Select the country, time zone, and keyboard layout.

Create a password and enter an email.


!!! info "Email Entry"
    The server will send emails to the entered address in case of critical system errors. If receiving alerts is not necessary, you can enter a dummy email.

![](../prox-creds.png)

Select the correct network interface and enter a hostname. The hostname with a proper domain is important only if you plan to create clusters or expose Proxmox to the internet. For homelab use, you can enter any hostname you like. For the IP address, Gateway, and DNS server, the default options are sufficient.

![](../prox-network.png)

Confirm the chosen settings and wait for Proxmox to install.

![](../prox-summary.png)

After the installation, the system will reboot to the TTY, which will display the server's address. Navigating to this address in any browser will allow you to enter the previously created credentials and access the Proxmox Web UI. At this point, the system is ready for creating VMs and LXC containers.

![](../prox-ui.png)
