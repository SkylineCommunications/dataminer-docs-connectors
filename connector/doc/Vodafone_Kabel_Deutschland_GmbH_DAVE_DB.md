---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_DAVE_DB
description: Explore DAVE DB in DataMiner, including connector capabilities, operational benefits, and use cases.
---

# Vodafone Kabel Deutschland GmbH DAVE DB

## About

The Vodafone Kabel Deutschland GmbH DAVE DB connector communicates with the Digital Audio Video Environment database. It retrieves node data and provides table actions to maintain database items.

## Key Features

- **Authenticated Database Access**: Connect to the database and select the polling stage after authentication.
- **Per-Node Polling**: Adjust each node's state and polling interval, or request a hard refresh.
- **Table Management**: Add, update, and delete items through table context menus, subject to Service-Names restrictions.

## Use Cases

### Managing DAVE Database Information

**Challenge**: Different database nodes need separate polling settings and accessible maintenance actions.

**Solution**: The connector uses a poll queue with per-node controls and exposes supported item actions in table context menus.

**Benefit**: You can tailor data retrieval and maintain database items from DataMiner.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_DAVE_DB_Technical).
