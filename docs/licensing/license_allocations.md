---
layout: default
title: License Allocation
nav_order: 1
parent: Licensing
---

# License Allocation <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i> <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 
{:.no_toc}

## Applicable Environments 
{:.no_toc}
- All

## Goal
{:.no_toc}
The goal of this activity is to evaluate license growth and needs using the built in "License Monitor" application. At the same time, Qlik Sense administrators should check to ensure its working and collecting usage data. 

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

### Check License Monitor Status <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

In the QMC, select **Tasks**:

[![Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png](images/Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png)

Find the "Reload License Monitor" Task and check if the status is "Success"

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png)

If the status is "Failed" then download the script log to see where it might be failing

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png)

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png)

Also consult help.qlik.com for assistance in configuring the monitoring tools


