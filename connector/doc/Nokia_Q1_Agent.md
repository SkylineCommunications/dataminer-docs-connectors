---
uid: Connector_help_Nokia_Q1_Agent
---

# Nokia Q1 Agent

## About

This is a DataMiner connector for the **Nokia Q1 Agent**, the network management system that is designed to manage Nokia node devices of the **Nokia DCNA** system. With this connector, you can monitor the Nokia node device data with DataMiner's alarm monitoring and trending features. Each node device will be displayed as a **Dynamic Virtual Element** (DVE) in the DataMiner user interface, for more intuitive monitoring.

### Key Features

- **FTP XML file import for node devices**: Importing your node devices is very easy. Configure the FTP information to import the XML file from the FTP server, and with just one click the node device DVE will be created.
- **Alarm monitoring of the node devices**: Each alarm triggered in the node devices can be monitored in real time.

## Use Cases

### Node Device Alarms Monitoring

**Challenge**: The **Nokia DCNA** system uses an obsolete communication protocol, and it is hard to monitor the alarm for each of the node devices when there is a large number of node devices.

**Solution**: With this connector, you can easily import the node devices, and each node device can be monitored individually. This also enables proactive monitoring and reduces the risk of unexpected system failures.

**Benefit**: Potential issues can be quickly addressed in real time, improving the reliability and performance of managing the Nokia DCNA system.

## Prerequisites

- **DataMiner version 10.2 or higher** is required.
- A **node device XML file** is needed for the creation of the DVE.
- **FTP server access credentials** are required to allow the connector to access the FTP directory.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Nokia_Q1_Agent_Technical).

