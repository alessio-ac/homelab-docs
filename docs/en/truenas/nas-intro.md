# File Server

## System info

- **OS:** TrueNAS Scale
- **IP:** 192.168.1.194
- **CPU:** Intel Core i3-6100 @ 3.70GHz
- **RAM:** 8GB DDR3
- **Network:** 1000Mb/s
- **Storage:** 
    1. 2x10TB Western Digital 3.5" HDD (*RAID1*)
    2. 120GB Crucial SSD (*boot*)

## Storage

RAID1 is the only available solution with two disks that allows me to have redundancy.

To monitor the health of the disks, I have set up full pool scrubs and periodic S.M.A.R.T. tests. The automated tests follow this schedule:

- **Scrub**: at 04:00 AM on the 1st and 15th of each month
- **Long S.M.A.R.T.**: at 04:00 AM on the 2nd and 16th of each month
- **Short S.M.A.R.T.**: at 04:00 AM on the 7th, 12th, 22nd, and 27th of each month


## File share

The pool is divided using ZFS datasets based on the determined usage. The datasets are shared on the network via NFS for Linux systems and SMB for Windows systems.

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
