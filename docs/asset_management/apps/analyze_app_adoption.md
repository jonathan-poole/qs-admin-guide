---
layout: default
title: Analyze App Adoption
parent: Apps
grand_parent: Asset Management
nav_order: 5
---

# Analyze App Adoption <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

<span class="label prod">production</span>

|                                  		          | Initial | Recurring |
|---------------------------------------------------------|---------|-----------|
| <i class="far fa-clock fa-sm"></i> **Estimated Time**   | 15 Min  | 5 min     |

Benefits:

  - Understand adoption
  - Better understand user-base
  - Identify top and bottom applications by adoption
  
-------------------------

## Goal
{:.no_toc}
At it simplest, the goal of this page is to identify the top five and bottom five applications by two metrics:
  
  - Total sessions
  - Total distinct users
  
It is then also important to identify any visible trends of usage -- is usage trending up or down, or are there consistent spikes? In addition, it is helpful to characterize these applications, e.g. _highly used yet only by a few inidividuals_, _widely used but infrequently_, etc. To visualize these areas, two additional charts will be built.

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

## Suggested Prerequisites

- [Remove/Quarantine Unused Apps](remove_quarantine_unused_apps.md)

-------------------------

## Operations Monitor

Please refer to the [Operations Monitor](../../tooling/operations_monitor.md) page for an overview and relevant documentation links.

-------------------------

## Confirm License Monitor is Operational

Navigate to the **Monitoring apps** stream and open up the **Operations Monitor** application.

[![app_adoption_17.png](images/app_adoption_17.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/app_adoption_17.png)

First and foremost, it is essential to confirm that the **Operations Monitor** is operational and up to date. Ensure that it is by selecting the _Show app information_ button, and then viewing the _Data last loaded_ section of the application's description. Alternatively, one could also check the task status in the QMC.

[![app_adoption_18.png](images/app_adoption_18.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/app_adoption_18.png)

## User & Session Metrics

Select the _Session Details_ sheet.

[![app_adoption_19.png](images/app_adoption_19.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/app_adoption_19.png)
