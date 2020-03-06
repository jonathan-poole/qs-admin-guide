---
layout: default
title: Notification of Unused Base/Community Sheets
parent: Apps
grand_parent: Asset Management
nav_order: 3
---

# Notification of Unused Base/Community Sheets <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>
{:.no_toc}

## Applicable Environments
{:.no_toc}
- Production (w/ Self-Service Enabled)

## Goal
{:.no_toc}
There are three primary goals:
  - Remove (or consider modifying) "Base" sheets that are not being used. This will focus down your applications and remove clutter, while also increasing performance of the site.
  - Keep "Community" sheets under control. In large environments where self-service is enabled, both private (personal sheets on a published application), and community sheets can grow rapidly out of control -- especially if the application's base sheets doesn't offer what the end-user is looking for, causing them to create their own sheets.
  - Finding out "why" users are not using certain base sheets and/or why they are creating and publishing many community sheets, as that content could potentially be made part of the standardized application.

** Note that "Private" sheets should be handled a bit differently--please refer to: [Remove Unused Private Sheets](remove_unused_private_sheets.md)

## Table of Contents
{:.no_toc}

* TOC
{:toc}

-------------------------

## Audit Activity Log <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>

As of the **fill in release here** release, the **Audit Activity Log** capability is now enabled, which allows for the tracking of who is accessing what sheets in applications. This enables the ability to measure sheet adoption as well as manage the amount of sheets in the applications--keeping them trimmed to only what is being leveraged.

This logging must be enabled on _every engine_ that the information is desired from, and is turned on by default on supporting releases.

[![notification_unused_sheets_native_1.png](images/notification_unused_sheets_native_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_1.png)

-------------------------

## Identification of Unused Sheets

This usage information is then surfaced inside of the **Operations Monitor** on the **Sheet Usage** sheet.

[![notification_unused_sheets_native_2.png](images/notification_unused_sheets_native_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_2.png)

As an example, we'll select the Telemetry Dashboard application on one of our rarely used internal servers, and we can see that the _App Profiling_ base sheet hasn't been accessed in, actually almost exactly one year.

[![notification_unused_sheets_native_3.png](images/notification_unused_sheets_native_3.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_3.png)

It is suggested that the administrator would add the **App Owner** field to the **Sheet Usage** table, as this table already contains the relevant information needed to report on usage, and the owner field is need to know who to contact.

[![notification_unused_sheets_native_4.png](images/notification_unused_sheets_native_4.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_4.png)

As far as the time range for sheets that are unused (or minimally used), it is suggested to select the _'> 90 days'_ value from the **Latest Activity Range** field -- though this range is ultimately up to the organization.

[![notification_unused_sheets_native_5.png](images/notification_unused_sheets_native_5.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/apps/images/notification_unused_sheets_native_5.png)

-------------------------

## Suggested Actions

Once the table has been built out and the filters and time ranges have been decided upon, it is suggested to then contact the owners either manually or programmatically via something like NPrinting. It is advised that it should be the owner's responsibility to decide what to do with these unused sheets. The app owners can then be responsible for contacting the community sheet owners for their individual cleanup. Base sheets should be considered the most critical sheets to address, with community sheets following.

In addition to the above, it is entirely possible that users aren't leveraging sheets because they potentially aren't positioned (ordered) properly, users are unaware of them, users don't understand how to leverage them, or users possibly aren't interested in the data presented on them. Rather than simply remove them, is is encouraged for the app owners to understand _why_ they are not being leveraged to better the applications and overall Qlik experience.

-------------------------

## Bulk Base/Community Sheet Removal <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

The below script snippet requires the [Qlik CLI](../../tooling/qlik_cli.md).

**When possible, one should always remove base and community sheets manually, leaving that responsibility to the owner of the applications. That being said, if there are potentially thousands of sheets that need to be removed, and this is the first time the organization is starting this management process, it is possible to programmatically remove these assets. This would generally be a one-time operation, as it is suggested to do this process monthly, which should be able to be maintained incrementally.**

The script below will tag any base or community sheets with the tag _'UnusedBaseOrCommunitySheet'_. It expects a csv file as an input, where the name of the column with the **Sheet Id** is specified.

### Script to Tag Unused Base/Community Sheets
```powershell

<insert awesome rad script here>
```

Once the script has been run above, and a review of the tagging has been confirmed as correct, the script below can be run to **permanently delete** these base/community sheets. **This process cannot be reversed.**

### Script to Delete Tagged Sheets
```powershell

<insert awesome rad script here>
```

**Tags**

#monthly
