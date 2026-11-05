---
uid: Connector_help_OneWeb_PCN_Collector
---

# OneWeb PCN Collector

The **OneWeb PCN Collector** connector retrieves and organizes **Predicted Cause Notifications (PCNs)** and their associated alarms from a Kafka server. These PCNs help identify the root causes of network issues. The connector is designed for NOC teams to monitor and analyze network events efficiently.

## About

### Version Info

|Range          |Features                                                                                  |Based on |System Impact            |
|---------------|------------------------------------------------------------------------------------------|---------|--------------------------|
|1.0.0.x [SLC Main] |- Initial release of the connector.<br>- Consumes PCN data via Kafka.<br>- Includes a tree control for viewing PCNs and their associated alarms. |-       |-      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a Kafka-based virtual connection and does not require manual input during element creation.

### Initialization

The **Configuration** page contains fields for Kafka authentication settings. These must be configured after the element is created to enable the connector to connect to the Kafka server and start polling for PCN data.

## How to use

The **OneWeb PCN Collector** organizes **PCN** and alarm data into three main areas for easy access:

- **General page**: Provides a tree control where you can select a specific PCN and view its details, along with its associated alarms, so that you can quickly navigate and analyze the data.
- **PCN Table**: Displays information about PCNs, including their ID, predicted cause, timestamp, and the number of associated alarms.
- **Alarms Table**: Lists all alarms retrieved by the connector. Each alarm includes details such as severity, timestamp, and a reference to the related PCN.

## Notes

To enable additional Kafka logs for debugging purposes, adjust the **DataMiner Debug logging level** to **Level 1**. Note that no data traffic will appear in the **Stream Viewer** as the connector relies entirely on Kafka for data retrieval.
