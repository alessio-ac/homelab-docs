 
# TrueNAS Scale Configuration

## Creation of admin user

On the first boot, the local IP of the server will be shown on the TTY. By entering this address on any browser, it will be possible to access the Web interface of the server.

![](../tty.png)

Create a password for the *admin* user.

![](../creds.png)

## Disk management

### Pool

Now that we have access to the TrueNAS dashboard, it is necessary to set up the storage. The following instructions explain how to create a mirrored configuration, however, there are many types of configurations possible depending on the number of disks.

Click on the *Storage* menu on the left, and then *Create Pool*.

From this screen, you will be able to name the pool.

![](../pool-name.png)

Select *Mirror* as the Layout, and let the automatic disk selection set up the rest.

![](../pool-disk.png)

If necessary also set up these devices:

- LOG ZFS*
- spare disk
- cache L2ARC
- Metadata
- Deduplication

Once everything necessary is selected, press *Create Pool*.

### Dataset

The pool now has a *root* by default, which can be divided into multiple datasets. These datasets can function as filesystems, each capable of storing data with specific permissions.

!!! info "Warning"
    Datasets are not the only available option, *zvols* are virtual block devices with a pre-set size. They are usually used with the iSCSI file-sharing protocol.

To create a new Dataset, click on *Datasets* in the left menu and click *Add Dataset*

From here, just name the dataset and press *Save*.

![](../dataset-name.png)

It is possible to create infinite datasets based on the necessary uses. They can be created under existing datasets to make the pool more readable and organized.

## File sharing

Now that we have created the necessary datasets, it’s time to make them accessible on our network.

### Protocols

You can use different protocols for sharing. In this case, I will use NFS, beacuse it has the best Linux compatibility.

First, you need to start the necessary services for the sharing protocols to work. Click on *System Settings*, and in the submenu that opens, click on *Services*. From here, enable the necessary protocols and check the *Start Automatically* box to ensure they are ready at server startup. In my case, I will click on NFS.

![](../share-protocol.png)

### Share creation

From the menu, press *Shares*, and select *Add* based on the protocol to be used.

![](../create-share.png){align=left}

![](../add-share.png){align=right style="height:500px"}

Select the path of the dataset you want to share, enter a description of the share, and specify the network on which the share will be available.

At this point, you need to modify the dataset permissions to make it writable.

Go to the *Dataset* menu, select the dataset to modify, and click on *Edit* under *Permissions*. On the opened page, select *Write* for *Group* and *Other*, and press *Save*.

![](../dataset-permission.png){style="width:475px"}


### Mounting the share

To access the share simply mount it with the `mount` command on a Linux terminal.

```
sudo mount -t nfs 192.168.1.206:/mnt/test-pool/documents ~/Documents/share/ 
```