---
layout: default
title: Review/Update Capacity Plan
nav_order: 1
parent: System Planning
---

# Review/Update Capacity Plan
{: .no_toc }

## Applicable Environments
{:.no_toc}

- Production

## Goal
{:.no_toc}

This page is intended to act as an example of what a high-level capacity plan could look like. It is assumed that the organization would build one themselves with some of the below considerations in mind, or would work with Qlik's Services organization to have one defined/executed.

1. Document current state and expected state of several asset groups, which helps for planning
2. Document and justify the actions that are needed for capacity/architecture changes

It's important for stakeholders, budgetholders, and Qlik deployment owners to have advance notice when addition resources will be needed. This exercise helps you prepare for those requests and demonstrate the need. 

-------------------------

## Capacity Planning Process

There are four primary pillars that this process covers:

  - Licenses
  - Users
  - System
  - Applications

-------------------------

## Capacity Planning Example

The below is a high-level mockup of what a capacity plan's output could look like, including the four points from the Capacity Planning Process. For details on how to locate/calculate these metrics, please refer to the associated process item above.

**ACME Corp**

### Licenses

|                  | Licensed | Allocated | Remaining |
|------------------|----------|-----------|-----------|
| **Professional** | 50       | 44        | 6         |
| **Analyzer**     | 200      | 180       | 20        |

#### Actions

1. Analyze the allocated licenses for possible re-assignment.
2. Expand licenses to 75 Professional and 325 Analyzer.

### Users

|                  |  Peak    | Total     | +6 Months*| +12 Months* |
|------------------|----------|-----------|-----------|-------------|
| **Concurrency**  | 43       | 224       | 300       | 400         |

\* estimated numbers

#### Actions

1. Review system specs to see how it is performing with the above currently, and how it could scale.

### System

|                  | Engine CPU | Engine RAM |  Batch Window | Intra-day Reloads | Users per Proxy |
|------------------|------------|------------|---------------|-------------------|-----------------|
|                  | Good       | Good       | Good          | 30                | 35              |

#### Actions

1. Going to begin offloading intra-day reloads to an isolated scheduler.

### Application

Review App Metadata Analyzer for heavily used applications that are large/complex. Identify potential targets for app pinning and optimization.

#### Actions

Identified three applications for optimization and two applications for app pinning.
