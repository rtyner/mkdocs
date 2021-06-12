![alt text](https://seeklogo.com/images/M/microsoft-azure-logo-85055C44BE-seeklogo.com.png)

[Exam Objectives](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3VwUY "Exam Objectives")

# AZ-900 Azure Fundamentals

#### Cloud Service Models

* IaaS
  * Actual servers being provided by Azure
  * Scaling is fast
  * Only pay for what you use
  * No ownership of hardware
  * VMs, networks, building
* PaaS
  * Includes infrastructure
  * Middleware
	Tools
   * Supports the complete web app lifecycle
   * Avoids software license hell
* SaaS
   * Includes IaaS and PaaS
   * Provides a managed service
			§ Gmail, stripe, quickbooks
   * Pay an access fee to use
   * No maintenance and latest features
* Serverless
   * You don’t manage any servers
   * Azure Functions

#### Azure Marketplace
* Apps, VMs, templates, services

#### Cloud Architect Models
* Private - Azure on your own hardware
   * Services within the cloud are only offered to select users
   * Complete control of infra
   * Benefits of public cloud
   * Better security and privacy
   * Organizations IT is responsible for the cloud, not MS
* Public
   * No purchase of HW
   * Low monthly fees
   * Accessed from anywhere
* Hybrid
   * Private + Public
   * Avoids disruptions and outages
   * Regulatory 

### Azure Architecture

#### Regions and Availability Zones

* Regions
  * Region is a set of datacenters deployed within a latency defined perimeter and connected through a dedicated regional low-latency network
  * Each region has more than 1 datacenter
  * How to choose a region
		○ Location - close to users for low latency
		○ Features - no all features are available in all regions
		○ Pricing - pricing varies region per region
		○ Choose what is most important
  * Each region is paired with another region in the same geographic location
  * If a primary region has an outage, you can failover to the secondary region
  * Only one region in a pair is updated at a time
  * Some services use paired regions for replication

* Availability Zones
  * Each AZ is a physical location within a region
  * Each zone has its own power, cooling, and networking
  * Each region has a minimum of 3 zones

* Resource Groups - container that holds other resources
  * Everything in Azure is inside a resource group
  * Each resource can only exist in 1 resource group
  * You can add or remove resources to any resource group 
  * You can move a resource from one resource group to another 
  * Resources from multiple regions can be in one resource group
  * You can give users access to a resource group and everything in it
  * Resources can interact with outer resources in different resource groups
  * A resource group has a location, or region, as it stores metadata about the resources in it

* Azure Resource Manager (ARM)
  * Manages everything with creating or deleting resources
  * You can deploy manage and monitor resources as a group
  * Deploying resources will always result in the same results
  * Define dependencies between resources to make sure they work
  * Built in access control
  * Tag resources to ID them for future scenarios
  * Use tagging to stay on top of billing

* Creating Azure Resources
  * Can be done in Azure Portal, Powershell, or AzureCLI

### Compute

* VMs - virtualized HW that you control - priced per hour
* Scale Sets - sets of identical VMs that get created and deleted automatically
* App Services - managed platform for you to host your applications
* ACI - Azure Container Instances - hosts and runs your containers 
* Kubernetes - Orchestration of container images and applications CLUSTERS AND PODS
* Windows Virtual Desktop - virtual desktop in the cloud
* Functions - serverless compute, code that does one function

* Scale Sets
  * Lets you create and manage a group of identical, load balanced VMs
  * Auto scaling and scheduled scaling of resources
  * No extra cost for HAVING scaling, just for the resources used when scaling is necessary
  * A baseline VM is used as the template for the scaled ones

* App Services
  * Fully managed platform
  * Webapps
  * Webapps for containers - deploy and run containerized applications in Azure
  * API App - expose and connect your data backend
		○ Other applications connect programmatically

* Azure Container Instances
  * Self contained applications with all of the dependencies 
  * Less overhead than VMs
  * More portable, can be deployed to multiple hardware and OS platforms
  * Scaling and patching is simpler
  * ACI - Primary Azure service for running containers
  * User containerized applications to process data on demand by creating container image when you need it
  * Works with Azure portal, Azure cli, and powershell

* Azure K8s Services
  * Open source container orchestration system for automating application deployment, scaling, and management
  * Replicate container architectures
  * Standard Azure services included
  * Global reach

* Azure Container Registry (ACR)
  * Keeps track of current container images
  * Manages files and artifacts for containers
  * Feeds container images to ACI and AKS
  * Uses Azure identity and security features

* Windows Virtual Desktop
  * 100% virtualized Windows 10 desktop
  * Multiple users can use the same VM instance
  * Access anywhere
  * Secure storage of company data in Azure

* Functions - Serverless
  * Single function of compute
  * Called or invoked by a standard web address
  * Runs once and stops
  * Only runs when needed, saving money
  * If function fails, doesn't affect other services
App services are attached to an App Service Plan