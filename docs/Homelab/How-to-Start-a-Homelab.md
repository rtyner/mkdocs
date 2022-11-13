## Hypervisors - The software that will run the virtual machines (VM) for the lab 
- Type 1
	- [Proxmox](https://www.proxmox.com/en/proxmox-ve)
	- [ESXi Free](https://customerconnect.vmware.com/en/evalcenter?p=free-esxi8)
	- [XCP-ng](https://xcp-ng.org/)
- Type 2
	- [VirtualBox](https://www.virtualbox.org/)
	- [VMWare Workstation](https://www.vmware.com/products/workstation-pro.html)

## Networking
- Routers
	- [Opnsense](https://opnsense.org/)
	- [OpenWRT](https://openwrt.org/start)

## Prerequisites 
- SSH key created on your local computer
- Debian 11 ISO downloaded
- Windows Server 2022 ISO downloaded
- Windows 10 ISO downloaded
- Domain name for your Linux lab decided (example.lab.com)
- Domain name for your Windows lab decided (example.lab.com)
- A domain name on the internet

## Linux Skills
1. Setup a DHCP server or modify your current one to create a DHCP scope that will give you 50 IP addresses outside of this scope
2. Create a Debian 11 VM with 1GB of RAM and 1 vCPU. Set a static IP that is outside of your DHCP scope and change the hostname mkdocs.domain.com (replace domain.com with your chosen domain name)
	1. Create a user for yourself, add yourself to the sudoers group, and login to your new user
		1. You might want to look up what NOPASSWD is and what it does, and decide if you want to change that setting
	2. Install updates and the packages listed below an
		1. `python3 python3-pip vim git curl wget unzip`
	3. Enable unattended upgrades
	4. Deny root login over SSH and disable password login over SSH
	5. Disconnect from the Debian VM and reconnect with your local user using an SSH key
	6. Install [MkDocs](https://www.mkdocs.org/getting-started/)
	7. Enable the firewall and permit the ports for MkDocs and SSH, deny all other ports
	8. Verify you can access MkDocs from the browser on your local computer
	9. Document your network setup, and anything you need to remember from setting up this VM. This is now where all of the documentation you create for this will be stored.
	10. Determine how you are going to backup this VM and the rest of your VMs
3. Create 2 Debian 11 VMs with 4GB of RAM and 2 vCPUs in the same manner as above, name these docker-01.domain.com and docker-02.domain.com
	1. Figure out how to allow Ansible to connect to your new VM - https://docs.ansible.com/ansible/latest/user_guide/connection_details.html
	2. Install [Ansible](https://docs.ansible.com/ansible/latest/user_guide/index.html) on your local computer
	3. Create an Ansible playbook to configure your two new servers with below settings:
		1. Deny root login over SSH
		2. Disable password login over SSH
		3. Set this as the message of the day for the server - https://raw.githubusercontent.com/jwandrews99/Linux-Automation/master/misc/motd.sh
		4. Install the following packages `python3 python3-pip vim git curl wget unzip`
		5. Install `docker` and `docker-compose`
		6. Create a user for yourself
		7. Add your user to the docker group
	4. On docker-01 install the Pi-hole container by using a docker compose file
	5. Configure Pi-hole through the webui and add the blocklists at https://v.firebog.net/hosts/lists.php?type=tick
	6. On docker-02 install the Pi-hole container using a docker compose file
	7. Setup [Gravity Sync](https://github.com/vmstan/gravity-sync) to keep the two servers in sync
	8. Add the domain names of your 3 VMs to the Pi-hole local DNS, you can now resolve these hostnames in your browser
		1. From now on, when you create a service with a hostname, add it to the Pi-hole local DNS
	9. On docker-01 install and setup [Portainer](https://docs.portainer.io/start/intro)
	10. On docker-01 install and setup [Uptime Kuma](https://github.com/louislam/uptime-kuma)
		1. Configure Uptime Kuma to send alerts to a Discord server when one of your services loses connectivity
	11. On docker-02 install and setup [Dashy](https://github.com/lissy93/dashy)
		1. Configure [Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps) to allow secure access to Dashy from the internet using your internet facing domain name
		2. With Dashy secured, add your Pi-hole, Uptime Kuma, and MkDocs to Cloudflare Tunnels and add them to your Dashy dashboard
	12. Create an Ansible playbook to update all of your servers 
4. Create a GitHub account and add your SSH key to it
	1. Create a repository called Ansible and commit your playbook to it through the command line
	2. Create a repository called Docker and commit your docker-compose files to it through the command line
5. Publish your MkDocs documentation on GitHub using GitHub Pages
	1. Setup a custom domain for your documentation on GitHub - docs.domain.com
6. Configure GitHub Actions to automatically update your MkDocs website when changes are pushed to the repository

## Windows Skills

1. Create 4 Windows Server 2022 VMs and 1 Windows 10 VM. Set one up as the primary domain controller, one as the secondary domain controller, and join the other 2 to the domain as member servers
2. Create 4 Active Directory OUs. One for users, one for domain admins, one for groups, and one for computers
3. Create 2 standard users in AD named test1 and test2 with the GUI and place them in the users group
4. Create a Security Group and name it test-group, place this in the groups OU, add the test2 user to this group
5. Join your Windows 10 VM to the domain you created and place it in the computers OU
6. Create a domain admin in AD and add it to the domain admins OU with PowerShell
7. Create a reverse look up zone in DNS
8. Setup DNS scavenging
9. Setup DHCP on the primary domain controller and configure a DHCP scope
10. On the Windows 10 VM you created, install Remote Server Administration Tools (RSAT)
11. Open Active Directory Users and Computers from within [RSAT](https://learn.microsoft.com/en-us/troubleshoot/windows-server/system-management-components/remote-server-administration-tools) and take a look around, look at DHCP and DNS too - This is where most management is done
12. Determine what domain controller is holding the FSMO roles with the GUI, PowerShell, and the Windows command prompt
13. Install DFS and file server features on the 2 member servers
14. Create a file share on both servers with the same name and place a file in each share, with different names - testfile1 testfile2
15. Create a DFS namespace and add those shares to the name space
16. Create a DFS replication group, setup two way replication
17. Use Group Policy to map the DFS namespace when user test1 logs in
18. Use group policy to install Google Chrome and the uBlock Origin extension
19. Create a domain password policy in Group Policy
20. Print a list of all domain users using PowerShell and then filter that to show name only
21. Use PowerShell to see the date the password was last changed fort he user test1
22. Print a list of all domain computers using PowerShell and then filter that to show name only
23. Create 10 new users in AD from a CSV file using PowerShell
24. Use PowerShell to set the Company and Division of all of your users in AD (This is something I did just this last week)
25. Remove one of these users from AD using PowerShell