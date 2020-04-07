---
layout: default
title: Optimize License Allocation
nav_order: 1
parent: Licensing
---

# Optimize License Allocation <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i> <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 
{:.no_toc}

## Applicable Environments 
{:.no_toc}
- All

## Goal
{:.no_toc}
The goal of this activity is to evaluate license growth and needs using the built in "License Monitor" application. At the same time, Qlik Sense administrators should check to ensure its working and collecting usage data. 

There are a three recommendations that license allocations can be monitored and optimized. 

These are:

1 - Removing license allocations for users that have left the organization
2 - Removing license allocations for users that have not recently logged in or have never logged in
3 - Downgrading Professional allocations to Analyzer allocations for users who are not exercising their 'professional' capabilities

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------


### 1 - Removing license allocations for users that have left the organization  <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

To get a list of current allocations, go to the HUB , select the "Monitoring apps" stream and select the "License monitor" application

[![Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png](images/Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png)

From the 'App Overview' select 'New Sheet' 

[![Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet.png](images/Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet.png)

Give the new sheet a title of "Current License Allocations"

[![Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet_Title.png](images/Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet_Title.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_App_Overview_NewSheet_Title.png)

Click on the 'Current License Allocations' new sheet and then click the 'Edit' button on the toolbar

[![Optimize_License_Allocations_HUB_License_Monitor_EditSheet.png](images/Optimize_License_Allocations_HUB_License_Monitor_EditSheet.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_EditSheet.png)

Add a table from the chart library onto the empty sheet

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable.png)

Click the 'Add Dimension' button 

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddDimension.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddDimension.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddDimension.png)

Select 'User ID'

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddUserID.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddUserID.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_AddUserID.png)

Next, on the right side, under 'Dimensions' select 'Add Column' and choose 'Allocated Access Type'

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_AllocatedAccessType.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_AllocatedAccessType.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_AllocatedAccessType.png)

Uncheck 'Include Null Values'

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_ExcludeNullValues.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_ExcludeNullValues.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_ExcludeNullValues.png)

Next, on the right, click 'Sorting' and drag the 2nd column 'Allocated Access Type' above the 1st column 'User ID'. This will group the table by 'Allocated Access Type'

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_Resort.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_Resort.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Add_Resort.png)

A sample result is as follows.  You can make additional changes as you see fit to make it clear which userIDs have an allocated access type.

[![Optimize_License_Allocations_HUB_License_Monitor_AddTable_Resorted.png](images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Resorted.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_AddTable_Resorted.png)

Click 'Done' on the toolbar
 
[![Optimize_License_Allocations_HUB_License_Monitor_Done.png](images/Optimize_License_Allocations_HUB_License_Monitor_Done.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_Done.png)

The sample final result is as follows:

[![Optimize_License_Allocations_HUB_License_Monitor_CurrentLicenseAllocationsCOMPLETE.png](images/Optimize_License_Allocations_HUB_License_Monitor_CurrentLicenseAllocationsCOMPLETE.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Optimize_License_Allocations_HUB_License_Monitor_CurrentLicenseAllocationsCOMPLETE.png)


### 2 - Removing license allocations for users that have not recently logged in or have never logged in  <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

In this section, we import a customized Qlik Sense application 

### 3 - Downgrading Professional allocations to Analyzer allocations for users who are not exercising their 'professional' capabilities  <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

