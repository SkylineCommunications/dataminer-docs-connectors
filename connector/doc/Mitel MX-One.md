---
uid: Connector_help_Mitel_MX-One
---

# Mitel MX-One

## About

This is a DataMiner connector for the **Mitel MX-One**, an enterprise business communication. It is the central system that manages a company's phone calls and business communications which supports modern IP/SIP telephony as well as traditional PBX (Private Branch Exchange) equipment.

With this connector, you can monitor the data of the Mx-One with DataMiner's alarm monitoring and trending features. Each extension can be displayed as a **dynamic virtual element** (DVE) in the DataMiner user interface, for more intuitive monitoring.

### Key Features

- **Monitoring of each interface**: Monitor the operational status of each interface and generate alarms for fail states.
- **Monitoring of each trunk**: Monitor the operational status and configurations of each trunk and generate alarms when a trunk goes down.
- **Monitoring of each gateway**: Monitor the operational status of each gateway and generate alarms when it is down.
- **Monitoring of each extension**: Monitor the operational status and configurations of each extension and enable alarming capabilities on them.
- **Dynamic virtual element (DVE) configuration**: Every extension within the system can be represented as a DVE.

## Use Case: Radio Alarms Monitoring

**Challenge**: The Mitel MX-One has alarms coming from many extension within its system. This might make it hard to monitor the alarms for each of the extension.

**Solution**: With this connector, you can represent each extension as a DVE, so that it can easily be monitored individually.

**Benefit**: Potential issues can be quickly addressed in real time, improving the reliability and performance of managing each extension.
