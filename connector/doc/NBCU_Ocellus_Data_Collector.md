---
uid: Connector_help_NBCU_Ocellus_Data_Collector
---

# NBCU Ocellus Data Collector

**Ocellus Data Collector** is a real-time and historical measurement and intelligence platform for streaming TV that provides solutions for the capture and analysis of QoE metrics oriented to user engagement validation. To retrieve the data, the connector uses an HTTPS connection.

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                     |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP or URL of the destination.
- IP port: The IP port of the destination.
- Bus address: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

To start using this connector, you need to specify the **User** name and the **Password** by clicking on the **Authentication** button on the **General** page .

Once you have logged in, you will need to especify the **App Name** on the **General** page.

### Redundancy

There is no redundancy defined.

## How to use


After the initialization process is completed, to set the data to be retrieved, you will need to add rows in both the **Top Level Metric Polling** and **Individual Metric Polling** tables, specifying the values to be retrieved. The connector will retrieve the requested data from the tables every minute, and this data will be available on the **Top Level Metric** and **Individual Metric** pages.
