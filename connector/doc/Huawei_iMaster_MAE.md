---
uid: Connector_help_Huawei_iMaster_MAE
---

# Huawei iMaster MAE

## About

The Huawei iMaster MAE connector integrates the Huawei iMaster MAE-Access management system into DataMiner. It ingests SNMPv3 alarm and heartbeat traps forwarded by the iMaster MAE northbound interface and enriches the picture with a daily network element (NE) inventory retrieved over SFTP.

This connector gives operators a real-time view of alarms raised across the managed access network, tracks the availability of the northbound feed through a heartbeat watchdog, and maintains an up-to-date inventory of all network elements.

## Key Features

- **SNMPv3 trap ingestion**: Receives and processes alarm traps from the iMaster MAE northbound interface in real time, presenting them in a dedicated Alarms Overview table with severity and alarm status.

- **Heartbeat watchdog**: Monitors periodic heartbeat traps and derives a device availability state, so a loss of the northbound feed is detected and can be alarmed even when no alarm traps are arriving.

- **Daily inventory synchronization**: Automatically downloads the daily NE inventory CSV export over SFTP and refreshes a full inventory table, with an on-demand "Force Update" option.

- **Alarm template ready**: Key status parameters are monitored so alarm severities can be assigned through DataMiner alarm templates.

## Use Case

**Challenge**: Operators managing a large Huawei access network need a single, real-time view of alarms and network element inventory, without logging into the iMaster MAE system directly.

**Solution**: Use the Huawei iMaster MAE connector to ingest northbound SNMP traps and synchronize the daily inventory export into DataMiner, consolidating alarms and inventory in one place.

**Benefit**: Faster alarm response, continuous visibility into the health of the northbound feed, and an always-current inventory of managed network elements.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Huawei_iMaster_MAE_Technical).
