---
uid: Connector_help_Starlink_Enterprise_API_V2_Migration
---

# Starlink Enterprise API V1 to V2 Migration Guide (DataMiner)

![Starlink API V2 Architecture](~/connector/images/StarlinkEnterpriseApiMigrationV2Diagram.png)

## Quick Summary

- **Objective**: Seamlessly migrate from Starlink API V1 to API V2
- **Goal**: No data loss and minimal operational impact
- **Approach**: Decouple API communication from aggregation and visualization

## Overview

Starlink API **V1 has reached End of Life**, and API **V2** is now the supported integration model.

To support API V2's **per-account authentication**, the DataMiner architecture has evolved into a **two-layer model**:

- **Starlink Enterprise Account elements** handle all API V2 communication.
- A central **Starlink Enterprise** element aggregates and visualizes data.

This migration is designed to be **non-disruptive**, preserving historical data, trending, and alarms.

## What Changes

| Area | API V1 | API V2 |
|------|--------|--------|
| Authentication | Shared Client ID | Client ID and Secret per account |
| Polling | Centralized | Per account |
| Scalability | Manual tuning | Native scalability |
| Architecture | Single tier | Decoupled |

## Migration Steps (Existing Systems)

### 1. Prepare Account Elements

For each Starlink account:

1. Create an element using the **Starlink Enterprise Account** connector.
1. Generate an **API V2 Client ID and Secret** for that account.
1. Configure the credentials on the Account element.
1. Set the **Target Aggregator** to your existing **Starlink Enterprise** element.

At this stage, no polling will start yet.

### 2. Required Naming Convention

Each account element must be named `Starlink Account <account name>`

This is required for future control actions.

### 3. Switch Protocol Range

1. Stop the existing **Starlink Enterprise** element(s).
1. Go to **Protocols & Templates**.
1. Set protocol range **1.1.0.x** to **Set as Production**.

### 4. Edit and Save Aggregator

Perform **Edit \> Save** on the **Starlink Enterprise** element to clear obsolete communication settings.

### 5. Activate the New Setup

1. Restart the **Starlink Enterprise** element(s).
1. Account elements detect the aggregator automatically.
1. Polling starts from the account layer.
1. Data is aggregated as before.

Migration complete with no data loss

## Post-Migration Benefits

- Improved scalability
- Better API stability
- Clear separation of responsibilities
- Safer authentication model
