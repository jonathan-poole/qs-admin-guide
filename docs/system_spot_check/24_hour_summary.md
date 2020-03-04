---
layout: default
title: Review 24 Hour Summary (Ops Monitor)
parent: System Spot Check
nav_order: 4
---

# Review 24 Hour Summary (Ops Monitor) <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i>
{: .no_toc }

## Applicable Environments
{:.no_toc}
- Production

## Goal
{:.no_toc}
The goal for this spot-check is use the [Qlik Sense Telemetry Dashboard](../../tooling/telemetry_dashboard.md) to review the last 24 hours of activity for the Qlik site. This will allow the administrator the ability to spot anomalies 

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

## Telemetry Dashboard - Details <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

Open the Qlik Sense Telemetry Dashboard application and navigate to the **Details** sheet. Inside this sheet, drill to the most recent day (since this task is a daily task), select the relevant **Request Filters**, and drill to the **Process Time** values which broach the threshold that you are interested in. Example:
