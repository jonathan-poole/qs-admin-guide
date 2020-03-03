---
layout: default
title: Check for New Apps
parent: Apps
grand_parent: Asset Management
nav_order: 1
---

# Check for New Apps <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

## Applicable Environments
- Development

## Goal
While the idea of simply checking for new applications seems relatively trivial and not particularly actionable, it is a good practice as it only takes a couple of minutes and could save you finding out about a very large app in a more unpleasant fashion (i.e. your engine node locking up). This page shows you two methods of visualizing/gathering that high-level application data on newly created applications so that you can be aware/potentially report on it.

--------------------------

## QMC - Apps <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

In the QMC, select **Apps**:

[![check_new_apps_native_1.png](images/check_new_apps_native_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_1.png)

In the upper right hand side of the screen, select the **Column selector**, and then selected the **File size (MB)** and **Created** columns. If you'd like to make the resulting table a bit more manageable, you can also optionally deselect additional columns like **Version** and **Tags**.

[![check_new_apps_native_2.png](images/check_new_apps_native_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_2.png)

Now select the filter icon for the **Created** column, and then select the filter of **Today** (or **Last seven days** if you'd like a slightly larger rolling window).

[![check_new_apps_native_3.png](images/check_new_apps_native_3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_3.png)

Lastly, you can review the resulting table and view any new apps, noting their file sizes. If any are particularly large, it might be worthwhile to follow-up with the owner of the application, and possibly do further analysis in with the App Metadata Analyzer.

[![check_new_apps_native_4.png](images/check_new_apps_native_4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/check_new_apps_native_4.png)

--------------------------

## Get List of New Apps (Qlik CLI) <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

```powershell
GC foo.txt
```

**Tags**

#weekly
