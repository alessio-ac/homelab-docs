# Nextcloud

Nextcloud è un servizio di cloud personale, simile a Google Drive, ma con il controllo completo dei propri dati.

- [Sito ufficiale](https://nextcloud.com/)
- [Documentazione ufficiale](https://docs.nextcloud.com/)

Lo utilizzo come gestore di file nel caso non sia su una macchina Linux. Offre la compatibilità con Joplin, programma per appunti che sincronizza tutte le note sul server.

In più, come Google Drive, offre una completa suite di programmi web per la modifica di documenti, chamata [Collabora](https://www.collaboraoffice.com/).

È attualmente installato su un LXC, tramite l'immagine di [TurnKey](https://www.turnkeylinux.org/nextcloud), disponibile direttamente dall'interfaccia di Proxmox.

Per dare accesso agli share NFS ho montato gli share direttamente su Proxmox, li ho impostati come "Mount Point" nell'LXC e tramite l'account Admin di Nextcloud ho impostato le cartelle richieste come "External storage". 

=== "Utilizzo"
    
    ![](/assets/collabora.gif)

=== "Configurazione LXC"

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

=== "Aggiunta degli share a Nextcloud"

    ![](/assets/nextcloud-admin.png)

