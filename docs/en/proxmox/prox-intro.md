# Hypervisor Server

## System info

- **OS:** Proxmox
- **IP:** 192.168.1.60
- **CPU:** Intel Core i7-6700 @ 3.40GHz
- **RAM:** 32GB DDR3
- **Network:** 1000Mb/s
- **Storage:** 
    - **/dev/nvme0n1**: WD Blue SN570 500GB SSD
    - **/dev/sda**: Samsung Enterprise 240GB SSD

## Virtual Machines

Proxmox is a virtualization platform based on Debian, using the Type 1 hypervisor KVM. I use this machine to virtualize various services useful for work, entertainment, and primarily for hobbies.

The following are all the installed virtual machines:

### **debian-docker**

VM that serves as the base for all Docker services, managed via Portainer.

- **ID**: 200
- **OS**: Debian 12
- **IP**: 192.168.1.151
- **vCPU**: 2
- **RAM:**: 4GB

### **media-server**

For all media-based services, connected to the `media` share. It has Jellyfin installed along with various scripts for media downloading.

- **ID**: 201
- **OS**: Debian 12
- **IP**: 192.168.1.156
- **vCPU**: 4
- **RAM:**: **4GB**

### **debian-remote**

Machine used solely for remote desktop.

- **ID**: 202
- **OS**: Debian 12
- **IP**: 192.168.1.235
- **vCPU**: 4
- **RAM:**: 4GB

## Containers

I also use the server for various LXC containers. These are much lighter than VMs and allow me to run various isolated services at a much lower performance cost.

- **100 (cloudflare-tunnel)**: Used to connect to the home network remotely.
- **103 (nextcloud)**: Personal cloud
- **105 (syncthing)**: File synchronization between devices
- **106 (bookstack)**: Knowledge base that I used primarily for my high school diploma
- **109 (wordpress)**: Private blog