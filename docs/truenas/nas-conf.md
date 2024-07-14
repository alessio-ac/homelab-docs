 
# Configurazione di TrueNAS Scale

## Creazione utente admin

Al primo avvio del server ci verrà mostrato sul TTY l'IP locale del server. Inserendo questo indirizzo su un qualunque browser sarà possibile accedere all'interfaccia web del server.

![](/assets/tty.png)

Dall'interfaccia Web verrà scelta una password per l'utente *admin*.

![](/assets/creds.png)

## Gestione dischi

### Pool

Adesso che abbiamo accesso alla dashboard di TrueNAS è necessario impostare lo storage. Le istruzioni che seguono spiegano come creare una configurazione *mirrored*, tuttavia ci sono molti tipi di configurazioni possibili in base al numero di dischi.

Cliccare sul menu a sinistra *Storage*, e di seguito *Create Pool*

Da questa schermata sarà possibile dare un nome alla pool.

![](/assets/pool-name.png)

Selezionare *Mirror* come Layout, e lasciare che la selezione automatica dei dischi imposti il resto.

![](/assets/pool-disk.png)

Se necessario impostare anche i dispositivi di:

- LOG ZFS*
- ricambio (*spare*)
- cache L2ARC
- Metadata
- Deduplicazione

Una volta selezionato tutto il necessario, premere *Create Pool*.

### Dataset

Le nuove pool hanno un dataset di *root* che si può dividere in più dataset sottostanti, ovvero dei filesystem che memorizzano dati con permessi specifici.

!!! info "Attenzione"
    I Dataset non sono l'unica opzione disponibile, gli *zvol* sono dei dispositivi a blocchi virtuali con una dimensione pre-impostata. Solitamente si utilizzano con il protocollo di condivisione file iSCSI.

Per creare un nuovo Dataset basata cliccare su *Datasets* nel menu a sinistra e cliccare *Add Dataset*

Da qui, basta dare un nome al dataset e premere *Save*.

![](/assets/dataset-name.png)

È possibile creare infiniti dataset in base agli utilizzi necessari. Si possono creare sottostanti a Dataset già esistenti per rendere più leggibile ed organizzata la pool. 

## File sharing

Adesso che abbiamo creato i dataset necessari è il momento di renderli accessibili sul nostro network.

### Protocolli

È possibile utilizzare diversi protocolli per lo sharing. In questo caso utilizzerò NFS, protocollo dedicato ai dispositivi con sistema operativo Linux.

Prima di tutto bisogna avviare i servizi necessari per far funzionare i protocolli di sharing. Cliccare su *System Settings*, e nel sottomenu che si apre cliccare su *Services*. Da qui abilitare i protocolli necessari e cliccare sulla spunta *Start Automatically* per fare in modo che siano già pronti all'avvio del server. Nel mio caso cliccherò su NFS.

![](/assets/share-protocol.png)

### Creazione share

Dal menu premere *Shares*, e selezionare *Add* in base al protocollo da utilizzare, nel mio caso utilizzerò NFS.

![](/assets/create-share.png){align=left}

![](/assets/add-share.png){align=right style="height:500px"}

Selezionare il percorso del dataset che vogliamo condividere, inserire una descrizione dello share, e inserire il network sul quale lo share sarà disponibile.

A questo punto, bisogna modificare i permessi del dataset per renderlo modificabile.

Andare sul menu *Dataset*, selezionare il dataset da modificare, e premere su *Edit* su *Permissions*. Dalla pagina aperta selezionare *Write* su *Group* e *Other*, e premere save.

![](/assets/dataset-permission.png){style="width:475px"}


### Montare lo share

Per accedere allo share appena creato e condiviso basta montarlo con il comando `mount` su un terminale Linux.

```
sudo mount -t nfs 192.168.1.206:/mnt/test-pool/documents ~/Documents/share/ 
```