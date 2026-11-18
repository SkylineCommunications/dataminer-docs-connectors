---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_DAVE_DB
description: "Explore key features and use cases of the Vodafone Kabel Deutschland GmbH DAVE DB connector for managing DAVE database nodes and items in DataMiner."
---

# Vodafone Kabel Deutschland GmbH DAVE DB

## About

The Vodafone Kabel Deutschland GmbH DAVE DB connector communicates with the Digital Audio Video Environment database. It retrieves node data and provides table actions to maintain database items.

## Key Features

- **Authenticated database access**: Connect to the database and select the polling stage after authentication.
- **Per-node polling**: Adjust each node's state and polling interval, or request a hard refresh.
- **Table management**: Add, update, and delete items through table context menus.

## Use Cases

### Managing DAVE Database Information

**Challenge**: Different database nodes need separate polling settings and accessible maintenance actions.

**Solution**: The connector uses a poll queue with per-node controls and exposes supported item actions in table context menus.

**Benefit**: You can tailor data retrieval and maintain database items from DataMiner.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_DAVE_DB_Technical).
