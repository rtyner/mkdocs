# Homelab

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
| hyperv-1.rtynerlabs.io            | 192.168.88.147   | Hyper V server                          |

#### Virtual Machines

| **Hostname**                      | **IP**           | **Description**                         |
| --------------------------------- | ---------------- | --------------------------------------- |
| vcsa.rtynerlabs.io                | 192.168.88.4     | vCenter server                          |
| rt-dc-1.rtynerlabs.io             | 192.168.88.5     | primary domain controller               |
| rt-autoctl.rtynerlabs.io          | 192.168.88.206   | automation - terraform, packer, ansible |
| rt-docker-1.rtynerlabs.io         | 192.168.88.241   | primary Docker host                     |
| rt-veeam-backup.rtynerlabs.io     | 192.168.88.243   | Veeam backup server                     |

#### Containers

| **Hostname**                      | **Host**         | **Exposed Port**    | **Description**                 |
| --------------------------------- | ---------------- | ------------------- | --------------------------------|
| unifi.rtynerlabs.io               | rt-docker-1      | 8443                | UniFi Controller                |
| portainer.rtynerlabs.io           | rt-docker-1      | 9000                | Portainer container management  |

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
