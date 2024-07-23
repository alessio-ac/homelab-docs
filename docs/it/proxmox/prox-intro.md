# VM Server

## Specifiche sistema

- **OS:** Proxmox
- **IP:** 192.168.1.60
- **CPU:** Intel Core i7-6700 @ 3.40GHz
- **RAM:** 32GB DDR3
- **Network:** 1000Mb/s
- **Storage:** 
    - **/dev/nvme0n1**: WD Blue SN570 500GB SSD
    - **/dev/sda**: Samsung Enterprise 240GB SSD

## Macchine virtuali

Proxmox è una piattaforma di virtualizzazione basata su Debian, utilizza l'hypervisor di Tipo 1 KVM. Utilizzo questa macchina per virtualizzare vari servizi utili per il lavoro, l'intrattenimento e, principalmente, per hobby.

Le seguenti sono tutte le macchine virtuali installate:

### **debian-docker**

VM che funge da base per tutti i servizi Docker, gestiti tramite Portainer.

- **ID**: 200
- **OS**: Debian 12
- **IP**: 192.168.1.151
- **vCPU**: 2
- **RAM:**: 4GB

### **media-server**

Per tutti i servizi basati sui contenuti multimediali, è collegata allo share `media`. Vi è installato Jellyfin e vari script per lo scaricamento di media.

- **ID**: 201
- **OS**: Debian 12
- **IP**: 192.168.1.156
- **vCPU**: 4
- **RAM:**: **4GB**

### **debian-remote**

Macchina utilizzata solamente per il remote desktop.

- **ID**: 202
- **OS**: Debian 12
- **IP**: 192.168.1.XXX
- **vCPU**: 4
- **RAM:**: 4GB

## Containers

Utilizzo il server anche per vari LXC. Dei container molto più leggeri rispetto alle VM che mi permettono di avere vari servizi isolati ad un costo di performance molto inferiore.

- **100 (cloudflare-tunnel)**: Utilizzato per collegarsi al network di casa anche da remoto
- **103 (nextcloud)**: Cloud personale
- **105 (syncthing)**: Sincronizzazione di file tra i dispositivi
- **106 (bookstack)**: Knowledge-base che ho utilizzato principalmente per la maturità
- **109 (wordpress)**: Blog privato