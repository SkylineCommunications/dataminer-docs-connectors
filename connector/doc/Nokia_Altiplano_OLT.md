---
uid: Connector_help_Nokia_Altiplano_OLT
---

# Nokia Altiplano OLT

## About

The **Nokia Altiplano OLT** is a virtual connector designed to interface with Nokia's Altiplano solution. It provides comprehensive visibility into the OLT (Optical Line Terminal) device by exposing key operational and configuration data. It provides a unified view of the device's hardware, interfaces, uplinks, and system performance, without requiring any configuration or control actions.

This connector gathers data from two complementary sources:

- **Kafka streams** for real-time operational and ONT (Optical Network Terminal) updates.
- **Altiplano API** for structured access to uplink and hardware information.

## Key Features

- **Dual data ingestion modes**: Supports both real-time Kafka streaming and periodic API polling for flexible data acquisition.
- **Device visibility**: Presents detailed information about hardware components, interfaces, and system performance metrics.
- **Reliable performance monitoring**: Continuously reflects the operational state of the system, including alarms and health indicators.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Nokia_Altiplano_OLT_Technical).
