---
layout: default
title: Check for New Apps
parent: Apps
grand_parent: Asset Management
nav_order: 1
---

# Check for New Apps <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>
{:.no_toc}

<span class="label dev">development</span><span class="label prod">production</span>

|                                  		                    | Initial | Recurring |
|---------------------------------------------------------|---------|-----------|
| <i class="far fa-clock fa-sm"></i> **Estimated Time**   | 5 Min   | 5 min     |

Benefits:

  - Awareness of new applications
  
-------------------------

## Goal
{:.no_toc}
While the idea of simply checking for new applications seems relatively trivial and not particularly actionable, it is a good practice as it only takes a couple of minutes and can increase reaction times to the presence of large applications. This page illustrates three methods of visualizing/gathering that high-level application data on newly created applications, so that the administrator can be aware/potentially report on it.

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

## QMC - Apps <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

In the QMC, select **Apps**:

[![check_new_apps_native_1.png](images/check_new_apps_native_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_1.png)

In the upper right hand side of the screen, select the **Column selector**, and then select the **File size (MB)** and **Created** columns. To make the resulting table a bit more manageable, optionally deselect additional columns like **Version** and **Tags**.

[![check_new_apps_native_2.png](images/check_new_apps_native_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2.png)

Now select the filter icon for the **Created** column, and then select the filter of **Last seven days**, or the desired range.

[![check_new_apps_native_3.png](images/check_new_apps_native_3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_3.png)

Lastly, one can review the resulting table and view any new apps, noting their file sizes. If any are particularly large, it might be worthwhile to follow-up with the owner of the application, and possibly do further analysis in with the App Metadata Analyzer.

[![check_new_apps_native_4.png](images/check_new_apps_native_4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_4.png)

-------------------------

## Operations Monitor

The following section leverages the **Operations Monitor**. Please refer to the [Operations Monitor](../../tooling/operations_monitor.md) page for an overview and relevant documentation links.

### Confirm License Monitor is Operational

Navigate to the **Monitoring apps** stream and open up the **Operations Monitor** application.

[![app_adoption_17.png](images/app_adoption_17.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/app_adoption_17.png)

First and foremost, it is essential to confirm that the **Operations Monitor** is operational and up to date. Ensure that it is by selecting the _Show app information_ button, and then viewing the _Data last loaded_ section of the application's description. Alternatively, one could also check the task status in the QMC.

[![app_adoption_18.png](images/app_adoption_18.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/app_adoption_18.png)

If the **Operations Monitor** is not properly configured, please refer to the [Operations Monitor Documentation](../../tooling/operations_monitor.md#documentation).

-------------------------

## Hub - Operations Monitor <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

Open up the Hub and navigate to the **Monitoring apps** stream. Select the **Operations Monitor** application.

[![check_new_apps_native_2_1.png](images/check_new_apps_native_2_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2_1.png)

From the **App overview** page, select the **Apps** sheet.

[![check_new_apps_native_2_2.png](images/check_new_apps_native_2_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2_2.png)

Select **Duplicate**, as a column will be added that isn't currently in a table.

[![check_new_apps_native_2_3.png](images/check_new_apps_native_2_3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2_3.png)

In **Edit** mode, select the **App Details** table, and add the **App Created Date** field.

[![check_new_apps_native_2_4.png](images/check_new_apps_native_2_4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2_4.png)

It is now possible to sort by that column to view new apps. In addition, feel free to add the **App File Size** field as well to filter by large applications only.

[![check_new_apps_native_2_5.png](images/check_new_apps_native_2_5.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2_5.png)

-------------------------

## Get List of New Apps (Qlik CLI) <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

The below script snippet requires the [Qlik CLI](../../tooling/qlik_cli.md).

The script will bring back any application that is greater than or equal to x days old _and_ greater than or equal to z bytes. The script will then store the output into a desired location in either csv or json format.

### Script
```powershell
# Function to collect applications that were created in the last x days over z size in bytes

# Parameters
# Assumes default credentials are used for the Qlik CLI Connection
$computerName = 'machineName'
$virtualProxyPrefix = '/default' # leave empty if windows auth is on default VP
$daysBack = 7
$byteSize = 0
$filePath = 'C:\'
$fileName = 'output'
$outputFormat = 'json'

# Main
$outFile = ($filePath + $fileName + '.' + $outputFormat)
$date = (Get-Date -date $(Get-Date).AddDays(-$daysBack) -UFormat '+%Y-%m-%dT%H:%M:%S.000Z').ToString()
$computerNameFull = ($computerName + $virtualProxyPrefix).ToString()
Connect-Qlik -ComputerName $computerNameFull -UseDefaultCredentials -TrustAllCerts

If ($outputFormat.ToLower() -eq 'csv') {
  Get-QlikApp -filter "createdDate ge '$date' and fileSize ge $byteSize" -full | ConvertTo-Csv -NoTypeInformation | Set-Content $outFile
  }  Else {
  Get-QlikApp -filter "createdDate ge '$date' and fileSize ge $byteSize" -full | ConvertTo-Json | Set-Content $outFile
} 
```

### Example Output
```
{
    "id":  "71c2361f-024b-4079-8487-5c442b50db8f",
    "createdDate":  "2020/03/03 16:04",
    "modifiedDate":  "2020/03/03 16:04",
    "modifiedByUserName":  "QLIK-POC\\dpi",
    "customProperties":  [

                         ],
    "owner":  {
                  "id":  "27a825fe-3cad-488a-9dcd-d436a90e319c",
                  "userId":  "dpi",
                  "userDirectory":  "QLIK-POC",
                  "name":  "dpi",
                  "privileges":  null
              },
    "name":  "New App!",
    "appId":  "",
    "sourceAppId":  "00000000-0000-0000-0000-000000000000",
    "targetAppId":  "00000000-0000-0000-0000-000000000000",
    "publishTime":  "1753/01/01 00:00",
    "published":  false,
    "tags":  null,
    "description":  "",
    "stream":  null,
    "fileSize":  139762,
    "lastReloadTime":  "1753/01/01 00:00",
    "thumbnail":  "",
    "savedInProductVersion":  "12.475.3",
    "migrationHash":  "21ecc792c56e18162f1785d3d41f28fdaced5c96",
    "dynamicColor":  "",
    "availabilityStatus":  "Available",
    "privileges":  null,
    "schemaPath":  "App"
}
```

**Tags**

#weekly
