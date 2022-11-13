# Network Information

## Network

| **Hostname**                 | **IP**     | **Description**          |
| ---------------------------- | ---------- | ------------------------ |
| opnsense.local.rtynerlabs.io | 10.1.1.0   | Oopnsense router         |
| ap1.local.rtynerlabs.io      | 10.1.1.226 | unifi ap running openwrt |
| core-sw-01                   | 10.1.1.254 | cisco ws-c3560g-24ps poe gigabit switch                         |

## Physical Hosts

| **Hostname**             | **IP**       | **Description**                    |
| ------------------------ | ------------ | ---------------------------------- |
| pve1.local.rtynerlabs.io | 10.1.1.2     | primary proxmox host               |
| pve2.local.rtynerlabs.io | 10.1.1.3     | secondary proxmox host               |
| truenas.local.rtynerlabs.io   | 10.1.1.6 | bare metal truenas hosting 2 zfs pools |

## Virtual Machines

| **Hostname**                      | **IP**     | **Description**                     |
| --------------------------------- | ---------- | ----------------------------------- |
| opnsense.local.rtynerlabs.io      | 10.1.1.1   | OPNSense router VM                  |
| docker-1.local.rtynerlabs.io      | 10.1.1.200 | primary docker host for testing     |
| traefik.local.rtynerlabs.io       | 10.1.1.9   | traefik reverse proxy               |
| nfs-file-1.local.rtynerlabs.io    | 10.1.1.22  | nfs file server hosting 15TB array  |
| dns-1.local.rtynerlabs.io         | 10.1.1.53  | pihole dns 1                        |
| dns-2.local.rtynerlabs.io         | 10.1.1.54  | pihole dns 2                        |
| arch-download.local.rtynerlabs.io | 10.1.1.21  | arch linux file transfer server     |
| ard-dev-1.local.rtynerlabs.io     | 10.1.1.25  | arduino development server          |
| nextcloud.local.rtynerlabs.io     | 10.1.1.20  | nextcloud file storage              |
| prod-docker-1.local.rtynerlabs.io | 10.1.1.10  | production docker host 1            |
| prod-docker-2.local.rtynerlabs.io | 10.1.1.11  | production docker host 2            |
| dc-1.win.rtynerlabs.io          | 10.1.1.55  | primary windows domain controller   |
| dc-2.win.rtynerlabs.io          | 10.1.1.56  | read only windows domain controller |
| win-clt-ws1.win.rtynerlabs.io                      | 10.1.1.57  | windows 10 client VM                |

## Containers

| **Name**            | **Host**      | **Exposed Port**     **Description** |                               |
| ------------------- | ------------- | ------------------------------------ | ----------------------------- |
| eclipse-mosquitto   | docker-1      | 1883,9001                            | mosquitto mqtt server         |
| smokeping           | docker-1      | 49154                                | smokeping network ping tester |
| heimdall            | docker-1      | 49155,49133                          | heimdall dashboard            |
| plex                | prod-docker-1 |   32400                                   |  plex media server                             |
| uptime-kuma         | prod-docker-1 | 3001                                 | uptime monitoring             |
| portainer           | prod-docker-1 | 8000,9443                            | portainer container manager   |
| calibre             | prod-docker-1 | 8080                                 | calibre document/ebook server |
| airsonic            | prod-docker-1 | 4040                                 | airsonic music server         |
| cloudflared         | prod-docker-1 |                                      | cloudflare tunnel             |
| tautilli            | prod-docker-1 | 8181                                 | plex stats                    |
| dashy               | prod-docker-1 | 8093                                 | dashy dashboard               |
| nginx-proxy-manager | prod-docker-1 | 80,443                               | nginx reverse proxy manager   |
| navidrome           | prod-docker-2 | 4533                                 | navidrome music server        |
| youtube-dl material | prod-docker-2 | 17442                                | youtube dl server             |
| phpipam             | prod-docker-2 | 8092                                 | ip address management         |