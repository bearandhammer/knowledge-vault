
## Section One - Intro
---

AZ-900.

![[Pasted image 20230116175455.png]]

What is the Cloud - lol:

![[Pasted image 20230116175543.png]]

---

Rough services:

![[Pasted image 20230116175704.png]]

Unlimited = virtually.

Exam page: https://learn.microsoft.com/en-us/certifications/exams/az-900

---

Virtual machines:
- Windows - create admin user.
- Linux - SSH keys.

---

Cert - never expires!!! For life.

---

Exam - skills measured:

![[Pasted image 20230116181158.png]]

---

## Sections - AZ-900
---

### Section 2: Describe Cloud Computing
---

***Describe cloud computing.***

#### Benefits of Cloud Computing

The ability to rent computing resources on demand - paying for what you use.

1000+ different services.

Web App - layer of abstraction. Easier to work with, no access to OS.
Function app - serverless.
Logic App - create small workflows (connecting processes).

Create resource -> shows popular services and services by category. Lew - check out the AI + Machine Learning services.

Compute - also contains Redis, Kubernetes and Docker (containers).

Marketplace - third-party resources available for use.

#### Shared Responsibility Model

How MS and the customer have divided responsibility for all sorts of things including security.

I guess this is true, we meet the provider in the middle (with responsibility to utilise supporting resources in a responsible manner). Azure will, of course, protect (by default) these resource (physical security, networking and encryption).

VMs - you need to update.
Web App/App Service - Azure responsible. Shared responsibility, to some degreee, for Network/Firewall, Application Settings and Auth platform. You are till responsible for devices, data and user accounts.

So different divides depending on the resource you select.

Cloud SaaS (software as a service). Office 365 - you don't control the application itself.

Tiers:

- VM = mixed.
- App Sevice = mixed/shared.
- SaaS = mixed/shared. Identity/accounts platform then shared. Further up abstraction chain.

On Prem.
IaaS - Infrastructure as a Service (VM Infrastructure - varies by service type).
PaaS - Platform as a Service (App Service).
SaaS - Software as a Service (Office 365).

As you move down these tiers more responsibility moves to the provide (mixed/shared).

![[Pasted image 20230116184649.png]]


#### Public Cloud, Private Cloud, Hybrid Cloud

Three types of cloud platform.

***Public Cloud - available for the general public.***

"The public cloud is defined as computing services offered by third-party providers over the public internet, making them available to anyone who wants to use or purchase them."

In this case, Azure owns the hardware, and their own network and infrastructure and they are making them available to the customer (to rent the services).

We are normally talking about the public cloud (9/10 scenarios).

***Private Cloud - available to select users instead of the general public***

"The private cloud is defined as computing services offered either over the Internet or a private internal network and only to select users instead of the general public."

Here, you are invited to be a part of it. E.g. a government cloud (e.g. they own, lease or have exclusive access to the hardware). 

Azure does provide private cloud software - Stack HCI (use on own hardware). Azure can also provide clouds with exclusive access (e.g. back into the government realm).

***Hybrid Cloud - as you would guess, it's a mixture of the public/private cloud

"A hybrid cloud...is a computing environment that combines a private cloud with a public cloud."

Many ways to cut this cake.

Example (and this is nuts, I have never seen this). A SQL Server 'stretch' database...where you have an on-premises SQL Server that, behind the scenes, has access to the cloud when it needs additional storage (deprecated now - but did pass me by).

*"Combination of public and private clouds; scale private infrastructure to the cloud."*

Exam - requires the classic compare and contrast!!!

There are some examples in the downloaded study guide - refer to this!

#### Cloud Pricing

Contraversal topic.....oooh!!!

Cloud pricing can be complicated - good lord can't it!

Several factors are involved, can be considered a bit of a downside.
- Difficult to predict monthly bill.
- Difficult to understand in advance what a service will really cost.
- Possibility for big savings but you lose predictability.

e.g. VM pricing is affected by:
- Region.
- Operation System SKU / License.
- Instance size. CPU/RAM.
- Disk type / size (multi-disks).
- Bandwidth (networking).
- Backup storage.
- Reservations / Savings Plan (things like reserved instances).
- Support agreement.

e.g. Cosmos DB
- API choice.
- Region/regions.
- Standard vs serverless.
- Ops per second (DTUs).
- Consumed storage.
- Optional dedicated gateway.
- Backup storage.

55+ services are free.
Some services have free tiers.
Some have throughput limits.

***Commonplace is to be charged by time***
OR ***pay by GB (storage)***
OR ***pay for throughput (operations) or traffic***

Throughput (operations) = ***pay for read, write, list or delete. Pay for messages or queries***. Usually minimal cost per operation. 

More esoteric - like DTUs!!!

### Section 3: Benefits of Cloud Computing

***Describe the benefits of using cloud services.***

#### Cost Savings Benefit of Cloud Computing

Here is the list of general, key benefits (will be covered in turn):

![[Pasted image 20230117181715.png]]

##### Cost Savings

Tools are provided to understand costs and to be able to control them.

![[Pasted image 20230117181907.png]]

Capex - up front expenditures (setup costs).
On-prem OPEX - on-going costs for on prem. Electicity, cooling, real estate, employees, fixing hardware, scaling, etc.

Azure transformation value - shows the savings over years (vs the on-premises costs).

It is (or should be) possible to save money.

Why is it cheaper then...
- MS can provision resources for cheaper than we can, period. Renewable energy, etc. = ***economies of scale***.
- e.g. MS can run server cheaper than anyone else (with a few exceptions).

It is also cheaper because we can use things like autoscaling to reduce the cost. With on-prem you need to (ideally) over provision, to predict future growth.

DB Servers are typically over provisioned!!! Interesting.

#### High Availability, Scalibility and Elasticity

***High availability*** - time system is operational (expressed as a percentage).

![[Pasted image 20230117182629.png]]

4 minutes a month of down time. Some services go way beyond this too.

100% uptime - this isn't really achievable.

***Scalibility*** - the ability of a system to handle growth of users or work.

***Elasticity*** - the ability of a system to automatically grow and shrink based on application demand.

![[Pasted image 20230117183046.png]]

Ultimately leads to cost savings.

#### Reliability and Predictability

***"Since you're giving up control of the platform, you need the cloud to be reliable".***

MS - publishes SLAs for services.

Financial guarantee of their performance - if their services don't meet expectations they will refund you 'some' of the costs for those services.

Azure - establised procedures for rollouts and regional recovery.

MS does provide tools to improve reliability.
- Availability Sets.
- Availability Zones.

MS also provides tools for backups and site recovery (disaster recovery).

What is this...test these failures using tools such as ***Chaos Studio***.

https://azure.microsoft.com/en-us/products/chaos-studio - useful in dev/staging.

Global Reach - able to deploy application into multiple geographical regions around the world.

OR - serve content at the edge (think CDN).

It's not possible for most businesses to run data centres in multiple countries.

#### Security, Governance and Monitoring

##### Security

Security - is massive and a full-time job! 

e.g. Use of AI/ML in products like Azure Firewall or Azure AD - to look for malicious attempts to access resources.

Identity is the number 1 attack vector; identity protection is key.

Azure - basic DDoS protection free (how does this compare to CloudFlare?). You can pay for more advanced DDoS protection.

https://www.g2.com/compare/cloudflare-inc-cloudflare-cdn-vs-azure-ddos-protection

##### Governance

The rules or regulations that the company places on the data/applications, aswell  as government/other auths rules.

GDPR - in europe, for example.

There are tools in Azure for governance:
- Azure Policy.
- Azure Blueprints.

You can make policies that apply to multiple subscriptions (across the org). Or create granular policies...

e.g. all VMs must have backups.
e.g. tagging convention for resources.

##### Monitoring

Monitor service - reporting/logging (alerts?).

Automation to act on events being monitored without human intervention being required. e.g. scaling to add extra VMs.

### Section 4: Cloud Service Types

***Describe cloud service types.***

#### IaaS, PaaS and SaaS

- ***IaaS*** - Infrastructure as a service.
- ***PaaS*** - Platform as a service.
- ***SaaS*** - Software as a service.
- ***Serverless***

![[Pasted image 20230117195604.png]]

![[Pasted image 20230117195630.png]]


##### Infrastructure as a service

***"IaaS is a type of cloud computing service that offers essential compute, storage, and networking resources on demand, on a pay-as-you-go basis."***

Least abstracted in many cases. 

Examples: VMs, networking, load balancers, firewalls. Essential services.

Virtualised versions of on-prem, in some cases.

##### Platform as a service

***"PaaS is a complete development and deployment environment in the cloud."***

Sometimes called cloud-native. Requires modification of application a bit to run under this model (more abstraction).

***"Like IaaS, PaaS includes infrastructure - servers, storage, and networking - but also middleware, development tools, business intelligence (BI) services, database management systems, and more. PaaS is designed to support the complete web application lifecycle: building, testing, deploying, managing, and updating."***

Upload code packages and have them run, without access to the hardware.

##### Software as a service

***"SaaS allows uers to connect to and use cloud-based apps over the internet. Common examples are email, calendaring, and office tools (such as Microsoft Office 365)."***

Calendaring??? Direct quote...

![[Pasted image 20230117201037.png]]

Access to applications on demand.

Portal itself is a SaaS application. Access to configuration only. Further abstraction in many cases.

##### Serverless

Consumption-based pricing model. Run on demand.

***"There are still servers...you just don't ever have to deal with them."***

Even more abstraction than PaaS. 

- Even with PaaS, you have to choose an App Service Plan. 
- With PaaS, scaling in your responsibility.
- Serverless means not worrying about choosing the right plan.
- Serverless means not worrying about scaling.
- Serverless means you might pay £0 if you don't use the service.

Other serverless offerings:
- Compute - Azure Functions.
- Compute - Serverless Kubernetes (Virtual Nodes w/ ACI).
- Database - Azure SQL Database Serverless.
- Database - Cosmos DB Serverless.

### Section 5: Core Architectural Components of Azure

This section accounts for 35-40% (which constitutes the largest section).

We are now discussion Azure-specifics (not generalised cloud benefits).

#### Regions

There are 60+ regions in the world. Not all regions are accessible to every customer.

Some are:
- Backup regions (requiring you to have services in one region specifically to use them).
- Some are isolated (e.g. country/government).
- Some have to be signed up.

New regions are always being announced. Azure has (at the time of writing) more  regions than any other provider.

#### Region Pairs

Not all regions have equally fast access to every other region. Pairs are configured to have fast connections between them.

So...pick one to run the services and then put backups in the pair.

***"Each region has one othr region which is treated as it's 'pair'.***

***Almost always in the same geographical location - data storage laws.*** 

***The data connection between regions pairs is the highest speed available.*** 

***Software rollouts are deployed to one region of a pair and the other is not touched.*** 

***If multiple regions go down, one region of each pair is treated as a priority."***

Example pairs:

![[Pasted image 20230118193057.png]]

#### Sovereign Regions

- Azure Government (US).
- China.

As you would expect. China - must have a contract with a business in contract. No deploying resources to China without a prior, special connection.

Germany - used to be a sovereign region. But no more. All europe is now generalised.

#### Availability Zones

![[Pasted image 20230118193524.png]]

Availability zone = the way that the region is organised. Not every region has availability zones. Most new regions have it.

Availability zone - compromies of one or more data centers.

Physical separation by building. Resilience (increase availability of an application) - SLA is higher on this kind of configuration. Planning required on application setup.

Regions with availability zones:

![[Pasted image 20230118193907.png]]

![[Pasted image 20230118193922.png]]

UK South is included.

#### Data Centers

Physically separate buildings with:
- Own power.
- Own internet/network.
- Own Cooling setups, etc.

Example region with availability zones:

![[Pasted image 20230118194156.png]]

Data centers do not, of course, have to be this close (it could be up to 50 kilometres away - there is a max distance)...

Real info (for availability zones/regions) in relation to distance:

![[Pasted image 20230118194405.png]]

![[Pasted image 20230118194435.png]]

#### Resource Groups

A way to logically groups resources. A way to act on them as one unit:

- Set security.
- Delete resources.
- Lock the resources.
- Set up policies.

The resources do not have to be in the same physical location to share a resource group.

Here is the general structure of an Azure setup (through Management Groups -> Subscriptions -> Resource Groups -> Resources).

![[Pasted image 20230118195324.png]]

Resources can only be part of one group.

Subscription - is the unit of billing. A single company could have one or more subscriptions, of course.

***"Users have access to one or more subscriptions, with different roles."***

***"All the resources consumed by a subscription will be billed to the owner."***

***Can be used to organise resources into completely distinct accounts.***

Single user account - having access to three subscriptions:

![[Pasted image 20230118200006.png]]

#### Management groups

These lie at the top of the organisational structure is Management Groups. This is a grouping of other Management Groups (linking to subscriptions). Groups can be nested.

- Have common policies.
- Have common roles and restrictions.
- Shared control!!!

![[Pasted image 20230118200518.png]]

### Section 6: Azure Compute and Networking Services

Exam part - ***Describe Azure compute and networking services.***

#### Azure Compute Services

- Compute services.
- Networking services.
- Storage services.
- Database services.

Compute services covered:
- Virtual Machines (VM).
- VM Scale Sets (VMSS).
- App services (Web apps).
- Azure Container Instances (ACI).
- Azure Kubernetes Service (AKS).
- Windows Virtual Desktop.

Compute - ***"Executing code" in the cloud***.

##### Virtual Machines

IaaS.

Take an existing machine from your environment into the cloud - a copy (this is allowed).

Windows or Linux operating systems - several of each flavour.

A "slice" of a physical machine shared with other customers.

Full control over it, as if it was your machine.

In AWS - called EC2.

VM Types - over 200 to chose from (wowzers!).
Number of CPU cores, CPU speed, RAM size, temporary disk size (and how many disks), IOPs, etc.

##### VM Scale Sets

VMSS.

![[Pasted image 20230124182514.png]]

All of this is provided for free BTW (you pay for the VMs, of course, but no the scale set functionality).

##### App Services (PaaS)

A new paradigm for running code in the cloud.

Give your code and configuration to Azure, and they will run it (with a promise of performance - no access to the hardware).

PaaS offering. Abstraction!

##### Containers

![[Pasted image 20230124182836.png]]

##### Azure Virtual Desktop

Desktop version of Windows that runs in the cloud.

Your software installed, your files - available from anywhere (can even see your desktop on iOS and Android, or from a browser).

Runs on Azure.

#### Azure Networking Services

Specific to the exam:
- Virtual Networks.
- VPN Gateway.
- VNet Peering.
- ExpressRoute.

***In AWS, a Virtual Network is called a Virtual Private Cloud (yay - the VPC!!!).***

##### Types of Networking Services

Four main types:
- Connectivity Services
- Protection Services.
- Delivery Services.
- Monitoring Services.

##### Connectivity

![[Pasted image 20230124183449.png]]

##### Protection - Security Section of the Course

- DDoS Protection - Distributed Denial of Service attack protection.
- Azure Firewall.
- Network Security Groups.
- Private Link.

##### Delivery - Not on the Exam

But be aware, for reference:

![[Pasted image 20230124184041.png]]

##### Monitoring - Management Tools Section of the Course

- Network Watcher.
- ExpressRoute Monitor.
- Azure Monitor.

Azure Monitor - is the only one on the exam.

#### Network Peering

##### Virtual Networks in Azure

Pretty secure by default

- Address space: e.g. 10.0.0.0/16 (/16 = is the range, in this case 65,000 ip addresses in the range!).
- Each one can be divided into subsets - 10.0.0.0/24 (available IPs, in the example, is 251). You are free to create subnets.
- 5 are reserved for Azure (of 256 per subset).

Virtual network to Virtual network comms - requires peering.

Each Virtual Network has a Peering configuration section. Each config must have:
- A name (for 'this' VN and the remote VN - two-way).
- Options for allowing/blocking traffic (various).

Once a peering configuration is added VNs can now communicate (two-way).

IP to IP resolution works (haven't dealt with private DNS/domain names, etc.).

One way connection - could delete the peering connection on the remote, for example.

This can be done in the same region or across regions. This is called Global Peering - cost implication for Global Peering (pay international rates for bandwidth - ingress and egress).

#### Public and Private Endpoints

Endpoints - whenever you create a resource in Azure it has different implications as far as network.

e.g. Storage - default - public access from all networks. Doesn't mean everyone has access - you still need credentials, etc.

Other options:
- Public access from selected virtual network (need creds at any rate).
- Disable public access and use private access (need creds at any rate).

For virtual networks (and storage), when you pick a subset a 'Microsoft.Storage' endpoint will be added. Options handled for you. Is a proxy on the subnet for the storage account.

For private, all public access can be stopped. Direct one-to-one routing. Does not just apply to storage accounts.

Is always going to be a security concern.

### Section 7: Azure Compute Demo

This section constitutes practical demos - but I'll take notes on each section.

##### Creating a Virtual Machine

For the exam - you don't need to know all of the particular settings when creating a resource. But, I did opt to follow along anyway!

##### Connecting to a Virtual Machine

##### Creating Azure App Services / Web Apps

##### Azure App Services in Action

### Other Resources

https://learn.microsoft.com/en-us/certifications/resources/az-900-sample-questions

