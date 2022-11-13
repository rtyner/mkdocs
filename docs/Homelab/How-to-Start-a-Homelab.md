1. Setup a DHCP server or modify your current one to create a DHCP scope that will give you 50 IP addresses outside of this scope
2. Create a Debian 11 VM with 1GB of RAM and 1 vCPU. Set a static IP that is outside of your DHCP scope and change the hostname mkdocs.domain.com (replace domain.com with your chosen domain name)
	1. Create a user for yourself, add yourself to the sudoers group, and login to your new user
		1. You might want to look up what NOPASSWD is and what it does, and decide if you want to change that setting
	2. Install updates and the packages listed below
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
	2. Create an Ansible playbook to configure your two new servers with below settings:
		1. Deny root login over SSH
		2. Disable password login over SSH
		3. Set this as the message of the day for the server - https://raw.githubusercontent.com/jwandrews99/Linux-Automation/master/misc/motd.sh
		4. Install the following packages `python3 python3-pip vim git curl wget unzip`
		5. Install `docker` and `docker-compose`
		6. Create a user for yourself
		7. Add your user to the docker group
	3. On docker-01 install the Pi-hole container by using a docker compose file
	4. Configure Pi-hole through the webui and add the blocklists at https://v.firebog.net/hosts/lists.php?type=tick
	5. On docker-02 install the Pi-hole container using a docker compose file
	6. Setup [Gravity Sync](https://github.com/vmstan/gravity-sync) to keep the two servers in sync
	7. Add the domain names of your 3 VMs to the Pi-hole local DNS, you can now resolve these hostnames in your browser
		1. From now on, when you create a service with a hostname, add it to the Pi-hole local DNS
	8. On docker-01 install and setup [Portainer](https://docs.portainer.io/start/intro)
	9. On docker-01 install and setup [Uptime Kuma](https://github.com/louislam/uptime-kuma)
		1. Configure Uptime Kuma to send alerts to a Discord server when one of your services loses connectivity
	10. On docker-02 install and setup [Dashy](https://github.com/lissy93/dashy)
		1. Configure [Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps) to allow secure access to Dashy from the internet using your internet facing domain name
		2. With Dashy secured, add your Pi-hole, Uptime Kuma, and MkDocs to Cloudflare Tunnels and add them to your Dashy dashboard
	11. Create an Ansible playbook to update all of your servers 
4. Create a GitHub account and add your SSH key to it
	1. Create a repository called Ansible and commit your playbook to it through the command line
	2. Create a repository called Docker and commit your docker-compose files to it through the command line
5. Publish your MkDocs documentation on GitHub using GitHub Pages
	1. Setup a custom domain for your documentation on GitHub - docs.domain.com
6. Configure GitHub Actions to automatically update your MkDocs website when changes are pushed to the repository