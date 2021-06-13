# Network Information

## **Local**

#### Network

| **Hostname**                      | **IP**           | **Description**                         |
| --------------------------------- | ---------------- | --------------------------------------- |
| usg.rtynerlabs.io                 | 192.168.88.1     | UniFi USG 3P primary gateway            |
| ap-1.rtynerlabs.io                | 192.168.88.201   | UniFi AP-AC Lite                        |
| ap-2.rtynerlabs.io                | 192.168.88.213   | UniFi AP-AC Lite                        |

#### Physical Hosts

| **Hostname**                      | **IP**           | **Description**                         |
| --------------------------------- | ---------------- | --------------------------------------- |
| esxi1.rtynerlabs.io               | 192.168.88.3     | primary ESXi host                       |
| hyperv-1.rtynerlabs.io            | 192.168.88.147   | Hyper V server, Windows file share      |

#### Virtual Machines

| **Hostname**                      | **IP**           | **Description**                         |
| --------------------------------- | ---------------- | --------------------------------------- |
| vcsa.rtynerlabs.io                | 192.168.88.4     | vCenter server                          |
| rt-dc-1.rtynerlabs.io             | 192.168.88.5     | primary domain controller               |
| rt-k8master1.rtynerlabs.io        | 192.168.88.40    | kubernetes master                       |
| rt-k8node1.rtynerlabs.io          | 192.168.88.41    | kubernetes node 1                       |
| rt-k8node2.rtynerlabs.io          | 192.168.88.42    | kubernetes node 2                       |
| rt-autoctl.rtynerlabs.io          | 192.168.88.206   | automation - terraform, packer, ansible |
| rt-docker-1.rtynerlabs.io         | 192.168.88.241   | primary Docker host                     |
| rt-veeam-backup.rtynerlabs.io     | 192.168.88.243   | Veeam backup server                     |

##### Planned
| **Hostname**                      | **IP**           | **Description**                         |
| --------------------------------- | ---------------- | --------------------------------------- |
| rt-plex.rtynerlabs.io             | 192.168.88.241   | plex mediaserver                        |
| rt-dns1.rtynerlabs.io             | 192.168.88.252   | primary unbound DNS server              |
| rt-dns2.rtynerlabs.io             | 192.168.88.253   | seconday unbound DNS server             |

#### Containers

| **Hostname**                      | **Host**         | **Exposed Port**    | **Description**                 |
| --------------------------------- | ---------------- | ------------------- | --------------------------------|
| unifi.rtynerlabs.io               | rt-docker-1      | 8443                | UniFi Controller                |
| portainer.rtynerlabs.io           | rt-docker-1      | 9000                | Portainer container management  |

##### Planned
| **Hostname**                      | **Host**         | **Exposed Port**    | **Description**                 |
| --------------------------------- | ---------------- | ------------------- | --------------------------------|
| pihole.rtynerlabs.io              | rt-docker-1      |                     | pihole DNS                      |
| proxy.rtynerlabs.io               | rt-docker-1      |                     | local reverse proxy             |
| ipam.rtynerlabs.io                | rt-docker-1      |                     | netbox ipam                     |
| monit.rtynerlabs.io               | rt-docker-1      |                     | grafana monitoring              |
| status.rtynerlabs.io              | rt-docker-1      |                     | status page                     | 
| syslog.rtynerlabs.io              | rt-docker-1      |                     | graylog syslog server           |

## Remote Hosts

| **rt-docker**                                                                                              | **rt-docs**                                                                                          |
|----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| <ul><li>Vultr High Frequency</li><li>Debian 10</li><li>4GB RAM</li><li>2 vCPU</li><li>128GB NVME</li></ul> | <ul><li>Vultr Compute</li><li>Ubuntu 20.04</li><li>1GB RAM</li><li>1 vCPU</li><li>25GB SSD</li></ul> |



| **Hostname**                            | **IP**           | **Description**     |
| --------------------------------------- | ---------------- | ------------------- |
| rt-docker.rtyner.com.beta.tailscale.net | 100.76.177.121   | Vultr Docker host   |
| rt-docs.rtyner.com.beta.tailscale.net   | 100.94.41.32     | MkDocs server       |

#### Remote Containers

| **Hostname**                           | **Host**         | **Exposed Port**    | **Description**                      |
| ---------------------------------------| ---------------- | ------------------- | --------------------------------|
| factorio.rtyner.com.beta.tailscale.net | rt-docker        | 34197               | Factorio server                 |
| proxy.rtyner.com.beta.tailscale.net    | rt-docker        | 81                  | NGINX reverse proxy             |
