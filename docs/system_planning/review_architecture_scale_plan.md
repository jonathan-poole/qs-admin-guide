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

The goal is to have documented Qlik architecture diagrams of n and n+1 deployments, as well as an understanding of high-level architectural concepts within Qlik.

This is integral for:

- understanding the deployment and how it is laid out
- planning for growth
- articulating change
- understanding resiliency & availability
- having documentation available to others

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

-------------------------

## Terminology

[![architecture-1.png](images/architecture-1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/architecture-1.png)

-------------------------

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

For information regarding the persistence layer (repository database and file share), please refer to [Persistence](https://help.qlik.com/en-US/sense-admin/February2020/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Deploy_QSEoW/Persistence.htm).

-------------------------

## High-level Scaling Concepts



-------------------------

## Architectural Diagram Core Requirements



-------------------------

## Planning for N+1 Architectures
