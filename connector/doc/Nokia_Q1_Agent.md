---
uid: Connector_help_Nokia_Q1_Agent
---

# Nokia Q1 Agent

## About

This is a DataMiner connector for the **Nokia Q1 Agent**, the network management system that is designed to manage Nokia node devices of the **Nokia DCNA** system. With this connector, you can monitor the Nokia node device data with DataMiner's alarm monitoring and trending features. The node devices will be displayed as a **Dynamic Virtual Element** in your DataMiner, to serve better alarming and monitoring purposes.

### Key Features

- **FTP XML file import for node devices**: Importing your node devices is very easy! Configure the FTP information to import the XML file from the FTP server with just one click, and the node device DVE will be created.
- **Alarm monitoring of the node devices**: To have real-time monitoring of the alarms that are triggered in the node devices.

## Use Cases

### Node Device Alarms Monitoring

**Challenge:** The **Nokia DCNA** system uses obsolete communication protocol, and it is hard to monitor the alarm for each of the node device from a large amount of the node devices.

**Solution:** With this connector, you can easily import the node devices. For each node devices can be monitored individually. This also enables proactive monitoring and reduces the risk of unexpected system failures.

**Benefit:** Potential issues can be quickly addressed in real time, improving the reliability and performance of managing the **Nokia DCNA** system.

## Prerequisites

- **DataMiner version 10.2 or higher** is required.
- **Node device XML file** is needed for creating the DVE.
- **FTP server access**: You must have a username, and password and configure the FTP information for the connector to be able to access the FTP directory to get the node devices for the monitoring.

## Technical Information

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Nokia_Q1_Agent_Technical).
