# Homebox

Homebox è un servizio per la gestione dell'inventario personale. Offre un'interfaccia web semplice da utilizzare ed un sistema di ID per tracciare ogni singolo oggetto.

- [Documentazione ufficale](https://hay-kot.github.io/homebox/)
- [Demo dimostrativa](https://homebox.fly.dev/)

È utile per tenere traccia di cavi, periferiche e componenti PC che attualmente non utilizzo.

È attualmente installato con Docker in una VM nel mio server hypervisor. La parte Docker viene gestita tramite Portainer.

=== "Docker compose"

    ``` yaml
    version: "3.4"

    services:
    homebox:
        image: ghcr.io/hay-kot/homebox:latest
    #   image: ghcr.io/hay-kot/homebox:latest-rootless
        container_name: homebox
        restart: always
        environment:
        - HBOX_LOG_LEVEL=info
        - HBOX_LOG_FORMAT=text
        - HBOX_WEB_MAX_UPLOAD_SIZE=10
        volumes:
        - homebox-data:/data/
        ports:
        - 3100:7745

    volumes:
    homebox-data:
        driver: local

    ```
    
=== "Screenshot"

    ![](/assets/homebox.png)