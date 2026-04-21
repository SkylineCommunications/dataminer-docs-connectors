---
uid: Connector_help_Starlink_Enterprise_-_API_V2_Migration
---

# Starlink Enterprise API V1 → V2 Migration Guide (DataMiner)

![Starlink API V2 Architecture](~/connector/images/StarlinkEnterpriseApiMigrationV2Diagram.png)

## Quick Summary

- **Objective**: Seamlessly migrate from Starlink API V1 to API V2
- **Goal**: No data loss and minimal operational impact
- **Approach**: Decouple API communication from aggregation & visualization

---

## Overview

Starlink API **V1 has reached End of Life**, and API **V2** is now the supported integration model.

To support API V2’s **per-account authentication**, the DataMiner architecture has evolved into a **two-layer model**:

- **Starlink Enterprise Account elements** handle all API V2 communication
- A central **Starlink Enterprise** element aggregates and visualizes data

This migration is designed to be **non-disruptive**, preserving historical data, trending, and alarms.

---

## What Changes

| Area | API V1 | API V2 |
|------|-------|-------|
| Authentication | Shared Client ID | Client ID & Secret per account |
| Polling | Centralized | Per-account |
| Scalability | Manual tuning | Native scalability |
| Architecture | Single-tier | Decoupled |

---

## Migration Steps (Existing Systems)

### 1. Prepare Account Elements

For each Starlink account:

1. Create an element using protocol **Starlink Enterprise Account**
2. Generate an **API V2 Client ID & Secret** for that account
3. Configure the credentials on the Account element
4. Set the **Target Aggregator** to your existing **Starlink Enterprise** element

> At this stage, no polling will start yet.

---

### 2. Required Naming Convention

Each account element must be named:

```
Starlink Account <account name>
```

This is required for future control actions.

---

### 3. Switch Protocol Range

1. Stop the existing **Starlink Enterprise** element(s)
2. Go to **Protocols & Templates**
3. Set protocol range **1.1.0.x** to **Set as Production**

---

### 4. Edit & Save Aggregator

Perform **Edit → Save** on the **Starlink Enterprise** element to clear obsolete communication settings.

---

### 5. Activate the New Setup

1. Restart the **Starlink Enterprise** element(s)
2. Account elements detect the aggregator automatically
3. Polling starts from the account layer
4. Data is aggregated as before

✅ Migration complete with no data loss

---

## Post-Migration Benefits

- Improved scalability
- Better API stability
- Clear separation of responsibilities
- Safer authentication model
