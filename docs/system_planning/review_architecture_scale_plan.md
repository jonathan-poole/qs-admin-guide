---
layout: default
title: Review Architecture/Scale Plan
nav_order: 3
parent: System Planning
---

# Review Architecture/Scale Plan
{: .no_toc }

## Applicable Environments
{:.no_toc}

- Production 

## Goal
{:.no_toc}

The goal is to have documented Qlik architecture diagrams of n and n+1 deployments*, as well as an understanding of high-level architectural concepts within Qlik.

This is integral for:

- understanding the deployment and how it is laid out

- planning for growth

- articulating change

- understanding resiliency & availability

- having documentation available to others


\* n refers to the current deployment, while n+1 refers to an anticpated state of the next deployment.

-------------------------

## Building an Architecture Diagram

### Core Requirements
- An editor. This could be Visio, PowerPoint, or web editors like [Gliffy](https://gliffy.com) and [Draw.io](https://draw.io).

- A set of base icons or symbols

  - If the deployment is on-premises
  
    - a server
        
    - a database
        
    - a file share
        
    - a network load balancer
    
  - If the deployment is in the cloud:
  
    - AWS icons can be found [here](https://aws.amazon.com/architecture/icons/)
    
    - Azure icons can be found [here](https://www.microsoft.com/en-us/download/details.aspx?id=41937)
    
    - GCP icons can be found [here](https://cloud.google.com/icons)
    
- Knowledge of what Qlik services are active on what nodes

- Knowledge of what each Qlik node is being used for

- Knowledge of where the Qlik file share is and the Qlik respository database is

- Server names and aliases

**Nice to Haves**

- Any network load balancers/interfaces in front of Qlik

- Any firewall settings pertinent to Qlik

### Example Diagrams

-------------------------

## Planning for N+1 Architectures



-------------------------

## Architectural Components

Qlik Sense Hub
  - Drag and drop development, analysis, and self-service environment.
  
Qlik Sense Management Console (QMC)
  - Centralized management of all aspects of a Qlik Sense deployment.
  
Qlik Sense Proxy (QPS)
  - Entry point into Qlik Sense for users and administrators.
  - Manages Authentication (last mile), manages sessions / license provisioning, able to load balance across engines.
  
Qlik Sense Engine (QES)
  - In-memory, associative data indexing engine.
  
Qlik Sense Scheduler (QSS)
  - Scheduling engine for application reloads from data sources.
  
Qlik Sense Repository (QRS)
  - Centralized storage of deployment information.
  
Qlik Sense Applications (.QVF)
  - Centralized storage of Applications before loading into memory, as part of a centralized SMB file share.

For additional documentation regarding the Qlik services, please refer to [Services](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Deploy_QSEoW/Services.htm).

-------------------------

## Terminology

[![architecture-1.png](images/architecture-1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-1.png)


## Load Balancing

When it comes to load balancing within the scope of Qlik, there are three general areas that are applicable:

1. Load balancing across Qlik proxies
  - Third-party network load balancer required
    - e.g. F5 BigIP, NGINX, Netscaler, AWS ALB, Azure Application Gateway, etc
  - Required for Qlik Proxy resilience
2. Load balancing across Qlik Engines
  - Native to Qlik at the proxy level
    - pure round robin
  - Option to plug in custom load balancer
3. Load balancing rules for applications
  - Native capability allows for "pinning" of applications to specific engines

For documentation/examples around load balancing rules, please refer to [Creating load balancing rules with custom properties](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Administer_QSEoW/Managing_QSEoW/create-load-balancing-rules-with-custom-properties.htm).

-------------------------

## Resiliency & High Availability

When speaking about resiliency and high availability within the context of Qlik architecture, there are three tiers to focus on:

1. Proxy/Engine Resiliency (consumption)
  - Requires 2+ Qlik proxy/engine nodes
  - Requires third-party network load balancer
  
2. Scheduler Resiliency (reloads)
  - Requires 2+ Qlik scheduler nodes
  
3. Site-wide High Availability
  - Requires both 1 and 2 from above
  - Requires decoupled repository database and decoupled file share
    - The repository database can be stream replicated or clustered for resiliency
    - The file share must be resilient
  - Requires 2+ Qlik nodes with all services enabled, with 1+ nominated as failover candidates
  
[![architecture-6.png](images/architecture-6.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-6.png)

For information regarding the persistence layer (repository database and file share), please refer to [Persistence](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Deploy_QSEoW/Persistence.htm).

-------------------------

## High-level Scaling Concepts

Broadly speaking, there are two primary scaling methodologies -- however, do note that these are not mutually exclusive:

1. Horizontal Scaling
  - Adding additional nodes/services, providing a wide, resilient topology.
  
2. Vertical Scaling
  - Expanding current server footprints, i.e. adding additional cores/RAM.

Horizontal scaling is typically common if a Qlik environment has small to medium sized applications with many users. Meaning, applications can be loaded quickly onto many different engines with little delay, and calculations are fast -- meaning that a shared cache isn't necessarily as integral for these applications. This methodology is also common in virtual environments on-premsises where VM sizes may be restricted. For instance, if an organization caps VM sizes at 96 or 128 GB of RAM, more than likely that Qlik environment will end up with a wider footprint, and will adopt practices to allow their applications to fit it.

Vertical scaling is typically common where the user base is not extensive, and the applications are quite large. Less nodes with larger capacity allows for larger applications with more users taking advantage of the same cache. These applications are usually [cache warmed](../tooling_appendix/cache_warming.md) so that they are readily available for users without delay.

Both of these methodologies are frequently combined when an organization has a mix of both very large apps and smaller apps with a wide user pool. It is usually common for organizations to have "small - medium app engines" and "large app engines" -- for example, maybe four of the former and two of the latter. Leveraging load balancing rules (as described above), large applications are "pinned" to the larger nodes, and vice versa.

-------------------------

## Example Production Architectures

[![architecture-2.png](images/architecture-2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-2.png)

[![architecture-3.png](images/architecture-3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-3.png)

[![architecture-4.png](images/architecture-4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-4.png)

[![architecture-5.png](images/architecture-5.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/system_planning/images/architecture-5.png)

For additional documentation and examples, please refer to [Qlik Sense Enterprise on Windows: multi-node deployment](https://help.qlik.com/en-US/sense-admin/February2020/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Deploy_QSEoW/Enterprise-deployment.htm).

