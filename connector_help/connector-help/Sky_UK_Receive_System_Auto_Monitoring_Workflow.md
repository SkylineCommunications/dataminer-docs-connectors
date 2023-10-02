---
uid: Connector_help_Sky_UK_Receive_System_Auto_Monitoring_Workflow
---

# Sky UK Receive System Auto Monitoring Workflow

Connector automating the process of uplink flow monitoring.

## About

Auto Monitoring is a transport stream analyzer driver which monitors multiple full uplink chains. The monitoring workflow is versatile and the driver allows for extensive configuration such as: including/excluding chains, enabling/disabling monitoring, choosing a tuning IRD, log configuration, and so on.

The key objective of the driver is to collect relevant data, tune the IRD and cross check the service list with the program list on the corresponding Sentry device. The whole process is being monitored, where the driver raises alarms in case any part of the chain is invalid.

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Make sure to visit the **Configuration** page before using the element. The *Tuning IRD* and *Station* parameters need to be entered for the correct monitoring flow.

## How to use

Make sure to follow the steps from the **Initialization** section on this page first. 
All the monitoring data can be found in the *Monitoring* table at the top of the **General** page. Individual chains can be included/excluded from the monitoring. The table also provides insight in the current status of the monitoring for each chain.

Key data for monitoring can be found in the **Output Stream Overview** table. You can verify the data which will be used to tune the IRD here.

The alarm statuses for each chain can be found in the **Chain Monitoring Results** table. From there, you can easily find the root cause of the alarm.

**Errors** page contains a table where all the issues related to the uplink flow occured. The operators can follow the proposed actions and acknowledge the issues.

For DataMiner related issues (e.g. stopped elements, invalid naming convention, etc.), **Log** page has all the entries. User can also disable these logs as needed.
