# File Server

## Specifiche sistema

- **OS:** TrueNAS Scale
- **IP:** 192.168.1.194
- **CPU:** Intel Core i3-6100 @ 3.70GHz
- **RAM:** 8GB DDR3
- **Network:** 1000Mb/s
- **Storage:** 
    1. 2x10TB Western Digital 3.5" HDD (*RAID1*)
    2. 120GB Crucial SSD (*boot*)

## Storage

RAID1 è l'unica soluzione disponibile con due dischi che mi permette di avere ridondanza.

Per tenere sotto controllo la salute dei dischi ho impostato degli scrub completi della pool e dei test S.M.A.R.T. periodici. I test automatizzati seguono il seguente programma:

- **Scrub**: alle 04:00 ogni 1 e 15 del mese
- **Long S.M.A.R.T.**: alle 04:00 ogni 2  e 16 del mese
- **Short S.M.A.R.T.**: alle 04:00 ogni 7, 12, 22 e 27 del mese


## File share

La pool è divisa tramite dataset ZFS in base all'utilizzo determinato. I dataset sono condivisi sul network tramite NFS per i sistemi Linux ed SMB per quelli Windows.

```
truenas-pool
├── Downloads
├── Files
├── ISOs
├── Media
│   ├── Music
│   ├── Pictures
│   ├── TV
│   └── Videos
└── Software
```
