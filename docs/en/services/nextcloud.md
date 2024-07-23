# Nextcloud

Nextcloud is a personal cloud service, similar to Google Drive, but with full control over your own data.

- [Official website](https://nextcloud.com/)
- [Official documentation](https://docs.nextcloud.com/)

I use it as a file manager when not on a Linux machine. It is compatible with Joplin, a note-taking app that synchronizes all notes to the server.

Additionally, like Google Drive, it offers a complete suite of web programs for document editing, called [Collabora](https://www.collaboraoffice.com/).

It is currently installed on an LXC container using the TurnKey image, available directly from the Proxmox interface.

To provide access to NFS shares, I mounted the shares directly on Proxmox, set them as mount points in the LXC, and added the required folders as "External storage" using the Admin account in Nextcloud.

=== "Usage"
    
    ![](../collabora.gif)

=== "LXC Config file"

    ``` yaml title="/etc/pve/lxc/103.conf"
    arch: amd64
    cores: 4
    features: nesting=1
    hostname: nextcloud
    memory: 2048
    mp0: /mnt/truenas/files,mp=/share/files,mountoptions=noatime
    mp1: /mnt/truenas/software,mp=/share/software,mountoptions=noatime
    mp2: /mnt/pve/isos,mp=/share/isos,mountoptions=noatime
    mp3: /mnt/truenas/pictures,mp=/share/pictures,mountoptions=noatime
    mp4: /mnt/truenas/music,mp=/share/music,mountoptions=noatime
    mp5: /mnt/truenas/videos,mp=/share/videos,mountoptions=noatime
    mp6: /mnt/truenas/tv,mp=/share/tv,mountoptions=noatime
    mp7: /mnt/truenas/downloads,mp=/share/downloads,mountoptions=noatime
    net0: name=eth0,bridge=vmbr0,firewall=1,gw=192.168.1.1,hwaddr=BC:24:11:F7:07:8D,ip=192.168.1.25/24,type=veth
    ostype: debian
    rootfs: nvme-lvm:vm-103-disk-0,size=16G
    swap: 512
    unprivileged: 1
    ```

=== "Adding shares to Nextcloud"

    ![](../nextcloud-admin.png)

