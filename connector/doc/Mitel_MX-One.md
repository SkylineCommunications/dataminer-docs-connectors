---
uid: Connector_help_Mitel_MX-One
description: "Learn how the Mitel MX-One connector monitors interfaces, trunks, gateways, and extensions in a DataMiner System."
---

# Mitel MX-One

## About

This is a DataMiner connector for the **Mitel MX-One**, an enterprise business communications system that manages phone calls and supports modern IP/SIP telephony as well as traditional PBX (Private Branch Exchange) equipment.

With this connector, you can monitor the data of the MX-One with DataMiner's alarm monitoring and trending features. Each extension can be displayed as a **dynamic virtual element** (DVE) in the DataMiner user interface, for more intuitive monitoring.

### Key Features

- **Monitoring of each interface**: Monitor the operational status of each interface and generate alarms for failure states.
- **Monitoring of each trunk**: Monitor the operational status and configurations of each trunk and generate alarms when a trunk goes down.
- **Monitoring of each gateway**: Monitor the operational status of each gateway and generate alarms when it is down.
- **Monitoring of each extension**: Monitor the operational status and configuration of each extension and generate alarms when appropriate.
- **Dynamic virtual element (DVE) configuration**: Monitor information for each system extension using a separate DVE.

## Use Case: Radio Alarms Monitoring

**Challenge**: The Mitel MX-One has alarms coming from many extensions within its system. This might make it hard to monitor the alarms for each of the extensions.

**Solution**: With this connector, you can represent each extension as a DVE, so that it can easily be monitored individually.

**Benefit**: Address potential issues in real time and improve the reliability of extension monitoring.
