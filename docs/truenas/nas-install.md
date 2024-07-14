# Installazione di TrueNAS Scale

!!! warning "Attenzione"
    La seguente guida è scritta per la versione **24.04.1.1** di TrueNAS SCALE, ed è stata effettuata su una macchina virtuale.


## Preparazione ISO

Scaricare l'immagine del sistema operativo dal sito ufficiale. È consigliato verificare la validità dell'immagine scaricata tramite i file forniti dal sito con PGP o SHA256.

Una volta verificata l'immagine va inserita all'interno di una memoria flash per poterla fornire al sistema di riferimento. È possibile farlo tramite `dd` su Linux:

```
dd bs=4M if=[PERCORSO ISO] of=/dev/[PERCORSO MEMORIA FLASH] conv=fsync oflag=direct status=progress
```

## Installazione

Inserire la memoria flash nel PC di riferimento e far partire il boot da essa tramite il boot menu (solitamente accessibile premendo F11 all'avvio del PC). Per l'installazione di TrueNAS è necessario disattivare il *secure boot*.

Al boot apparirà una schermata di selezione, basta aspettare 5 secondi e la prima opzione verrà scelta automaticamente.

![](/assets/boot.png)

Al primo menu mostrato dopo la sequenza di avvio selezionare *Install/Upgrade*

![](/assets/install-upgrade.png)

Scegliere il disco sul quale installare il sistema operativo. È consigliato usare **due** dischi di boot, per avere la sicurezza che il sistema rimanga operativo anche in caso fallisca uno dei due dischi. Nel mio caso sceglierò il disco virtuale `/dev/sdb`.

![](/assets/drive.png)

Confermare la selezione e creare selezionare la terza opzione per configurare l'utente *admin* dall'interfaccia Web.

![](/assets/admin.png)


Alla fine dell'installazione riavviare e dalla configurazione del BIOS scegliere il disco sul quale è stato installato TrueNAS come disco principale di avvio.