# Installazione di Proxmox

!!! warning "Attenzione"
    La seguente guida è scritta per la versione **8.2** di Proxmox, ed è stata effettuata su una macchina virtuale.

## Preparazione ISO

Scaricare l'immagine del sistema operativo dal sito ufficiale. È consigliato verificare la validità dell'immagine scaricata tramite i file forniti dal sito con PGP o SHA256.

Una volta verificata l'immagine va inserita all'interno di una memoria flash per poterla fornire al sistema di riferimento. È possibile farlo trmaite `dd` su Linux:

```
dd bs=4M if=[PERCORSO ISO] of=/dev/[PERCORSO MEMORIA FLASH] conv=fsync oflag=direct status=progress
```

## Installazione

Inserire la memoria flash nel PC di riferimento e far paritre il boot da essa tramite il boot menu (solitamente acessibile premendo F11 all'avvio del PC). Per l'installazione di TrueNAS è necessario disattivare il *secure boot*.

Al boot apparirà una schermata di selezione, basta aspettare 5 secondi e la prima opzione verrà scelta automaticamente.

Per prima cosa accettare l'EULA e selezionare il disco su cui verrà installato Proxmox. Nel mio caso */dev/sda*.

![](/assets/prox-drive.png)

Selezionare lo stato, il fuso orario e il layout della tastiera.

Creare una password ed inserire una mail.

!!! info "Inserimento mail"
    Il server invierà mail all'indirizzo inserito in caso di errori gravi nel sistema. Se non dovesse essere necessario ricevere gli avvisi è possibile inserire una mail finta.

![](/assets/prox-creds.png)

Selezionare la corretta interfaccia di rete, ed inserire un hostname. L'hostname con indirzzo di proprietà è importante solo se si ha intezione di creare cluster o di esporre proxmox all'internet, nel caso di utilizzo per homelab è possibile inserire un hostname a piacere. Per quanto riguarda l'indirizzo IP, il Gateway ed il server DNS, le opzioni di default vanno bene.

![](/assets/prox-network.png)

Confermare le impostazioni scelte e aspettare che Proxmox si installi.

![](/assets/prox-summary.png)

Dopo l'installazione il sistema si riavvierà sul TTY, il quale mostrerà l'indirizzo del server, navigando a qeull'indirizzo su un qualunque browser sarà possibile inserire le credenziali create prima ed accedere alla Web UI di Proxmox. A questo punto il sistema è pronto alla creazione di VM e LXC.

![](/assets/prox-ui.png)
