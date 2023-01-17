
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

Financial guarantee of their performance - if their services don't meet expectations

#### Security, Governance and Monitoring


---

### Other Resources

https://learn.microsoft.com/en-us/certifications/resources/az-900-sample-questions

