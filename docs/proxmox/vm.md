# Macchine Virtuali su Proxmox

Proxmox utilizza KVM, un modulo del kernel Linux che lo converte in hypervisor di tipo 1.

## Preparazione

Per creare una macchina virtuale è necessario ottenere prima l'immagine del sistema operativo che vogliamo usare sulla VM. Per questa guida utilizzero [*Debian 12*](https://www.debian.org/).


![](/assets/prox-iso.png){align=right style="height:230px"}

Dopo aver scaricato l'immagine cliccare su *local* nel menu a sinistra e *ISO Images* nel sottomenu, da qui premere su *Upload*, selezionare l'immagine appena scaricata ed aspettare che venga caricata sul server.

<br>

## Creazione della VM

Premere *Create VM* in alto a destra ed inserire il nome da dare alla macchina. Successivamente selezionare l'ISO appena scaricata dalla lista.


=== "Step 1"

    ![](/assets/prox-name.png)

=== "Step 2"
    
    ![](/assets/prox-select.png)

Selezionare *Q35* nel campo *Machine*, e *OVMF (UEFI)* per il *BIOS*. Per quanto riguarda il disco sul scrivere la partizioen EFI selezionare l'unica opzione disponibile al momento.

![](/assets/prox-system.png)

Per quanto riguarda il disco di boot è possibile configuraro il base all'utilizzo della VM, per questa guida lascierò i settaggi di default.

!!! info "Avvertenza per gli SSD"
    Se il disco sul quale verrà installa la VM è un SSD è consigliato abilitare l'opzione *Discard* e *SSD Emulation* nel menu avanzato.

![](/assets/prox-disk.png)

Nei prossimi menu specificare il numero di core e la quantità di memoria da associare alla VM.

!!! info "Tipo di CPU"
    In quasi tutti i casi è consigliato utilizzare il tipo *Host* per la CPU, in quanto è il più performante ed efficace, utilizzare altri tipi solo in caso il sistema operativo da installare richiede degli specifici tipi di CPU.

=== "CPU"

    ![](/assets/prox-cpu.png)

=== "Memoria"
    
    ![](/assets/prox-ram.png)

Confermare le impostazioni di default per il netowrk e il riassunto finale. A questo punto la macchina è pronta ad essere avviata. Per installare il sistema operativo è possibile procedere come su un qualunqe PC ed installare i necessari servizi seguendo le loro documentazioni.