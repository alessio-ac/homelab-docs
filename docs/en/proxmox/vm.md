# Virtual Machines on Proxmox

Proxmox uses KVM, a Linux kernel module that turns it into a Type 1 hypervisor.

## Preparation

To create a virtual machine, you first need to obtain the operating system image you want to use on the VM. For this guide, I will use [*Debian 12*](https://www.debian.org/).

![](../prox-iso.png){align=right style="height:230px"}

After downloading the image, click on *local* in the left menu and *ISO Images* in the submenu. From there, press *Upload*, select the downloaded image, and wait for it to be uploaded to the server.
<br>

## Creating the VM

Click *Create VM* in the top right and enter a name for the machine. Then, select the recently downloaded ISO from the list.


=== "Step 1"

    ![](../prox-name.png)

=== "Step 2"
    
    ![](../prox-select.png)

Select *Q35* in the *Machine* field, and *OVMF (UEFI)* for the *BIOS*. For the disk where the EFI partition will be written, select the only available option at the moment.

![](../prox-system.png)

For the boot disk, you can configure it based on the VM’s usage; for this guide, I will leave the default settings.

!!! info "Warning for SSDs"
    If the disk where the VM will be installed is an SSD, it is recommended to enable the *Discard* and *SSD Emulation* options in the advanced menu.

![](../prox-disk.png)

In the following menus, specify the number of cores and the amount of memory to assign to the VM.

!!! info "CPU Type"
    Typically, it is recommended to use the *host* CPU type, as it is the most performant and efficient. Use other types only if the operating system to be installed requires specific CPU types.

=== "CPU"

    ![](../prox-cpu.png)

=== "Memory"
    
    ![](../prox-ram.png)

Confirm the default network settings and the final summary. At this point, the machine is ready to be started. To install the operating system, you can proceed as on any PC and install the necessary services by following their own documentation.