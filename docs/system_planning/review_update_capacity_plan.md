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

1. Document current state and expected state of several asset groups, which helps for planning
2. Document and justify the actions that are needed for capacity/architecture changes

It's important for stakeholders, budgetholders, and Qlik deployment owners to have advance notice when addition resources will be needed. This exercise helps you prepare for those requests and demonstrate the need. 


-------------------------

## Capacity Planning Summary (Example)

**ACME Corp**

### Licenses

|                  | Licensed | Allocated | Remaining |
|------------------|----------|-----------|-----------|
| **Professional** | 50       | 44        | 6         |
| **Analyzer**     | 200      | 180       | 20        |

#### Actions

Analyze the allocated licenses for possible re-assignment.

### Users

|                  |  Peak    | Total     | +6 Months*| +12 Months* |
|------------------|----------|-----------|-----------|-------------|
| **Concurrency**  | 43       | 224       | 300       | 400         |

#### Actions

EOY

### System

|                  | Engine CPU | Engine RAM |  Batch Window | Intra-Day Reloads | Users per Proxy |
|------------------|------------|------------|---------------|-------------------|-----------------|
| **Concurrency**  | Good       | OK         | Good          | Good              | 35              |

#### Actions

RAM footprint currently at 40% of total RAM.  Expand by EOY.

### Application

Review App Metadata Analyzer for heavily used applications that are large/complex. Identify potential targets for app pinning.

#### Actions

Identified three applications for optimization and two applications for app pinning.
