---
layout: default
title: Remove/Quarantine Unused Apps
parent: Apps
grand_parent: Asset Management
nav_order: 2
---

# Remove/Quarantine Unused Apps <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>
{:.no_toc}
<span class="label dev">development</span><span class="label prod">production</span>

<i class="fas fa-clock fa-xs"></i>

|                   | Initial | Recurring |
|-------------------|---------|-----------|
| **Time Estimate** | 30 Min  | 5 min     |

## Top Benefits

- Reduce Maintenance
- Increase Performance

## Goal
{:.no_toc}
The goal of this procedure is to remove unnecessary (unused) applications from a Qlik site. This increases overall site performance, decreases clutter, and will focus users to what is pertinent.

## Applicable Environments
{:.no_toc}
- All

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------		

## Process

This task leverages the Operations Monitor application. The assumption is that the application is currently being reloaded each day. If there are issues with this reload or the application settings, please refer to the [Operations Monitor - Help Site](https://help.qlik.com/en-US/sense-admin/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Administer_QSEoW/Monitoring_QSEoW/Operations-monitor-app.htm) page for descriptions and troubleshooting of the app. 

1. Open the Operations Monitor App
2. Select the "Apps" sheet

[![quarantine_unused_apps_native_1.png](images/quarantine_unused_apps_native_1.png)](https://raw.githubusercontent.com/qs-admin-	guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_1.png)

3. In the App Details table object, sort by Last Accessed field and scroll to old dates or null dates 

[![quarantine_unused_apps_native_7.png](images/quarantine_unused_apps_native_7.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_7.png)

### Priority 1
    
Look for applications that are Published but have not been accessed. This can be quickly filtered to by selecting _Unpublished_ from the **Stream** column, and then by selecting _Select alternative_ to view all published applications.
	  
[![quarantine_unused_apps_native_2.png](images/quarantine_unused_apps_native_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_2.png)[![quarantine_unused_apps_native_3.png](images/quarantine_unused_apps_native_3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_3.png)
	  
[![quarantine_unused_apps_native_8.png](images/quarantine_unused_apps_native_8.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_8.png)
	  
### Priority 2
    
Look for applications that are Published and have not been used for a long time.
          
[![quarantine_unused_apps_native_4.png](images/quarantine_unused_apps_native_4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_4.png)
	  
### Priority 3	
    
Look for Unpublished applications that have not been used for a long time. Clear selections in the **Stream** field, and then select _Unpublished_ from the same field.
          
[![quarantine_unused_apps_native_5.png](images/quarantine_unused_apps_native_5.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_5.png)
	  
[![quarantine_unused_apps_native_6.png](images/quarantine_unused_apps_native_6.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/quarantine_unused_apps_native_6.png)

-------------------------

## Actions
    
1. If you don't already have a stream named "Quarantine", this is a good time to create one. Ideally, the stream should be walled off to only Content Admins or the like, where they can review the applications with their respective owners.

2. Contact the application owners to let them know you are moving their app(s) to Quarantine.	

3. Move the applications from Priorities 1, 2, and 3 to the Quarantine Stream

4. Any applications that have been in the Quarantine stream for X number of days can be removed (corporate policy on how long they should be kept.) It is considered a best practice to export them without data, at a minimum--potentially exported with data if the intent is to archive them.
	    

**Tags**
  
#monthly
