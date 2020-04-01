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

In the HUB, go to the "Monitoring Apps" stream and select the "License Monitor" App to open it

[![Analyze_Audit_License_Allocations_HUB_Monitoring_Apps_License_Monitor.png](images/Analyze_Audit_License_Allocations_HUB_Monitoring_Apps_License_Monitor.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_Monitoring_Apps_License_Monitor.png)

From App Overview, select the "Overview" sheet

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png)

Check the 'reload date' to see if the License Monitor has refreshed today

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_Overview_Date.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_Overview_Date.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_Overview_Date.png)

If the date is old , then you may be missing the latest license usage data. Skip to "debugging the License Monitor" below. 

If the data is within the last 24 hours then skip ahead to 'Analyzing the License Data' 



### Debugging the License Monitor <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

In the QMC, select **Tasks**:

[![Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png](images/Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_START_TASKS_Highlighted.png)

Find the "Reload License Monitor" Task and check if the status is "Failed". 

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_SUCCESS.png)

If you did not find the reload license monitor then either its been renamed or deleted. Simply recreate a new reload task. The default interval to refresh is every hour, but it can also be run less frequently. 

If the status is "Failed" then download the script log to see where it might be failing

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED.png)

SAMPLE error :  in the following example the script log shows a 401 error where a required data connection had the wrong credentials

[![Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png](images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_TASKS_Reload_License_Monitor_FAILED_Sample.png)

Also consult help.qlik.com for assistance in configuring the monitoring tools

https://help.qlik.com/en-US/sense-admin/February2020/Subsystems/DeployAdministerQSE/Content/Sense_DeployAdminister/QSEoW/Administer_QSEoW/Monitoring_QSEoW/Configure-monitoring-apps.htm


### Analyze License Data <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> 

First check the QMC to see how many total license are available for Professional and Analyzers. Go to the 'License Management' Section of the QMC. 

[![Analyze_Audit_License_Allocations_QMC_License_Management.png](images/Analyze_Audit_License_Allocations_QMC_License_Management.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_License_Management.png)

Ensure 'License Usage Summary' is selected on the right , and then check the total licenses on the left for both Professional and Analyzers

[![Analyze_Audit_License_Allocations_QMC_License_Management_UserMaximums.png](images/Analyze_Audit_License_Allocations_QMC_License_Management_UserMaximums.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_License_Management_UserMaximums.png)


Next, go to the 'Monitoring Apps' section of the QMC

[![Analyze_Audit_License_Allocations_QMC_MonitoringApps.png](images/Analyze_Audit_License_Allocations_QMC_MonitoringApps.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-
guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_MonitoringApps.png)

And select the 'License Monitor'

[![Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png](images/Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_QMC_MonitoringApps_LicenseMonitor.png)

Go to the 'Overview' sheet of the Qlik Sense "License Monitor" app

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview.png)

And select the 'License Monitor'

Click the 'Duplicate' Button on the toolbar

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_Duplicate.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_Duplicate.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_Duplicate.png)

Edit the 'User Timeline' Chart by selecting it and deleting the 'Access Type' Measure

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType.png)

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType_Delete.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType_Delete.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessType_Delete.png)

With 'Access Type' removed, open the 'Measures' and select 'Add Trend' under 'User Accessing Apps'

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend.png)

Select 'Linear' as the Trend Type

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend_Linear.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend_Linear.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddTrend_Linear.png)

Move the 'Allocation Changed in 7 days' table to the left and add a Filter Pane in the empty space to the left of the alterered 'User Timeline' chart


[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DragFilterPane.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DragFilterPane.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DragFilterPane.png)

Select 'Dimension' and choose 'Access Type'

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddAccessType.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddAccessType.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AddAccessType.png)

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessTypeAdded.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessTypeAdded.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AccessTypeAdded.png)

Now click 'Done' at the top 

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DoneButton.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DoneButton.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_DoneButton.png)

Select 'Analyzer' in the filter pane and view/analyze the growth rate in Analyzer app usage. To do this, grab two points on the chart that intersect with Y axis grid lines. In the sample below these two values are '20' and '30' respectively. Since the two points are 4 months apart , we can deduce that the linear growth rate is approximately 2.5 new analyzers per month. 

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AnalyzerTrend.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AnalyzerTrend.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_AnalyzerTrend.png)

Repeart for 'Professional'. In this sample, the growth line is flat. 

[![Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_ProfessionalTrend.png](images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_ProfessionalTrend.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/license/images/Analyze_Audit_License_Allocations_HUB_License_Monitor_App_Overview_ProfessionalTrend.png)











