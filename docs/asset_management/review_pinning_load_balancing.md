---
layout: default
title: Review Pinning/Load Balancing
nav_order: 9
parent: Asset Management
---

# Review Pinning/Load Balancing
{: .no_toc }

## Applicable Environments
{:.no_toc}
* Production

## Goal
{:.no_toc}

Both applications and tasks might warrant segregation for many reasons -- maybe that is for isolation of compute, e.g. there is a large application that should only run on certain "high capacity" hardware, or perhaps it is known that a task takes a high amount of compute and needs to be sent to a specific scheduler node. Other times, it might be warranted by different LOBs sharing the same site, and they each want dedicated nodes per LOB. Load balancing rules are a way of achieving that construct. 

The goal of this page is that by reading through (not necessarily following) the exercise on this page, that the Qlik administrator will have an understanding of how to leverage this capability, and can also review/compare their process with this page's.

The output of the [Capacity Plan](../system_planning/review_update_capacity_plan.md) should be a good indicator if this capability is necessary.

This page is intended to cover two topics:

  1. "Pinning" of applications to specific engine nodes
  
  2. "Pinning" tasks to specific scheduler nodes
  
These two areas will be supported specifically through the following examples:

  - Enabling apps to be hosted on dedicated nodes by stream
  
  - Enabling apps to be hosted on dedicated nodes individually
  
  - Enabling tasks to be run on specific nodes

## Table of Contents
{:.no_toc}

* TOC
{:toc}

-------------------------

## Example Exercise

### Create Custom Properties

1. Create the custom property **AppLevelUserNode** for application and node types with the following values:

  - UserNode1
  
  - UserNode2
  
  - UserNode3
  
2. Create the custom property **StreamLevelUserNode** for stream and node types with the following values:

  - UserNode1
  
  - UserNode2
  
  - UserNode3
  
3. Create the custom property **ReloadNode** for application and node types with the following values:

  - ReloadNode1
  
  - ReloadNode2
  
  - ReloadNode3
  
### Apply Custom Properties to Nodes


