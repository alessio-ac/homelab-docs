# Homebox

Homebox is a personal inventory management system. It offers a simple web interface and an ID system to track each individual item.

- [Official documentation](https://hay-kot.github.io/homebox/)
- [Demo](https://homebox.fly.dev/)

I use it to keep track of cables, peripherals, and PC components that I am not currently using.

It is currently installed with Docker in a VM on my hypervisor server. The Docker part is managed via Portainer.

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

    ![](../homebox.png)