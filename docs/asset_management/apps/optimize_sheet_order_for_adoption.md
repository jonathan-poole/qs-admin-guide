---
layout: default
title: Optimize Sheet Order for Adoption
parent: Apps
grand_parent: Asset Management
nav_order: 4
---

# Optimize Sheet Order for Adoption <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>
{:.no_toc}

## Applicable Environments
{:.no_toc}
* Production

## Goal
{:.no_toc}

When an application is developed, the sheets are ordered in a logical flow(Ex: DAR methodology); the sheet optimization should not overoptimize the flow. This page will help you optimize the application sheet order using the sheet usage data, and you must combine the usage data with the logical flow to make sure that the new sheet order will increase adoption rates and BI effectiveness.

## Table of Contents
{:.no_toc}

* TOC
{:toc}

-------------------------

## Suggested Prerequisites

- [Notification of Unused Base/Community Sheets](notification_unused_sheets.md)

-------------------------

## Audit Activity Log <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

As of the February 2019 release, the **Audit Activity Log** capability is now enabled, which allows for the tracking of who is accessing what sheets in applications. This enables the ability to measure sheet adoption as well as manage the amount of sheets in the applications--keeping them trimmed to only what is being leveraged.

This logging must be enabled on _every engine_ that the information is desired from, and is turned on by default on supporting releases.

[![notification_unused_sheets_native_1.png](images/notification_unused_sheets_native_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_1.png)

-------------------------

## Operations Monitor - Analyze Aplication Sheet Adopion  <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

It is possible to check the application's sheets usage using the Operations Monitor App.

In the Monitoring Apps stream, select **Operations Monitor**:

[![optimize_sheet_order_for_adoption01.png](images/optimize_sheet_order_for_adoption01.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption01.png)


//Add Selecting 5 Top Apps

Inside the Operations Monitor application there is a dedicated sheet to do the sheet usage analysis:

[![optimize_sheet_order_for_adoption02.png](images/optimize_sheet_order_for_adoption02.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption02.png)

Inside the **Sheet Usage** sheet you will be able to see all sheets across all the applications, for this example I will select an application named "Sample App":

[![optimize_sheet_order_for_adoption03.png](images/optimize_sheet_order_for_adoption03.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption03.png)

Now we can see all the sheets (Base Sheets, Community Sheets and Private Sheets) that we have inside the "Sample App" application.

[![optimize_sheet_order_for_adoption04.png](images/optimize_sheet_order_for_adoption04.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption04.png)

The sheet usage data can be exported and shared 

You should now use this data, combined with the logical flow, to reorder the sheets.


In this case since I want to keep using the 

Order | Sheet Name
------|--------------------------------
1     | Dashboard
2     | Inventory
2     | Sales Analysis by Region
3     | Expansion Analysis
4     | DSO

-------------------------

## Reorder Application Sheet

If we open the published "Sample App" application we can see that the original order do not correspod with the usage.

[![optimize_sheet_order_for_adoption05.png](images/optimize_sheet_order_for_adoption05.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption05.png)

To change that order by defaut the application owner should clone the "Sample App".

[![optimize_sheet_order_for_adoption06.png](images/optimize_sheet_order_for_adoption06.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption06.png)

As soon as the application gets duplicated it will be at Personal > Work area. Now we can edit the Base Sheets order.

[![optimize_sheet_order_for_adoption07.png](images/optimize_sheet_order_for_adoption07.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption07.png)

As soon as the application is open, make sure that the "Touch screen mode" feature is turned off.

[![optimize_sheet_order_for_adoption08.png](images/optimize_sheet_order_for_adoption08.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption08.png)

To move sheets we just need to drag and drop them to the desired order. In this case I will make sheet "Sales Analytis by Region" the second sheet.

[![optimize_sheet_order_for_adoption09.png](images/optimize_sheet_order_for_adoption09.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption09.png)

And the "Inventory" sheet the third sheet.

[![optimize_sheet_order_for_adoption10.png](images/optimize_sheet_order_for_adoption10.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption10.png)

Now the application sheet order is compliant with the usage data.

[![optimize_sheet_order_for_adoption11.png](images/optimize_sheet_order_for_adoption11.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/optimize_sheet_order_for_adoption11.png)

The "Sample App" now should be republished, replacing the old version.

**Tags**

#quarterly
