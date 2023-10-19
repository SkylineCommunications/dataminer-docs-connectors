---
uid: Connector_help_Sky_UK_Receive_System_Auto_Monitoring_Workflow
---

# Sky UK Receive System Auto Monitoring Workflow

This is a transport stream analyzer connector that monitors multiple full uplink chains. The monitoring workflow is versatile and the connector allows for extensive configuration such as including/excluding chains, enabling/disabling monitoring, choosing a tuning IRD, log configuration, and so on.

The key objective of the connector is to collect relevant data, tune the IRD, and cross-check the service list with the program list on the corresponding Sentry device. The whole process is being monitored, and the connector raises alarms in case any part of the chain is invalid.

## About

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

Before you start using the element, go to the **Configuration** page and configure the **Tuning IRD** and **Station** parameters for the correct monitoring flow.

## How to use

After you have correctly initialized the connector as described above, you will find all the monitoring data in the **Monitoring** table at the top of the **General** page. You can include or exclude individual chains from the monitoring. The table also provides insight in the current status of the monitoring for each chain.

Key data for monitoring can be found in the **Output Stream Overview** table. You can verify the data that will be used to tune the IRD here.

The alarm statuses for each chain can be found in the **Chain Monitoring Results** table. From there, you can easily find the root cause of the alarm.

The **Errors** page contains a table with all the issues that have occurred related to the uplink flow. You can follow the proposed actions and acknowledge the issues.

For DataMiner-related issues (e.g. stopped elements, invalid naming convention, etc.), you will find information on the **Log** page. You can disable these logs if needed.
