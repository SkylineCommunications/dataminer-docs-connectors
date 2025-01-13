---
uid: Connector_help_Nokia_NFM-P
---

# Nokia NFM-P

The Nokia NFM-P connector is used by Kordia to track the alarm events in the NFM-P network via XML API and JMS subscription.

The XML API is an NFM-P interface that provides an XML interface for the NFM-P through which an OSS client application can retrieve NFM-P network management information and receive event notifications from the NFM-P server using a persistent or non-persistent JMS connection.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Not applicable         |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

When the element has been created, on the **JMS Configuration** page, specify all the necessary arguments and then click the **Connect** button.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector uses SOAP calls to retrieve the device information and a JMS connection to receive alarm events.

### General Page

This page displays system-related information. The **JMS Connection** parameter shows the status of the connection (*Active* or *Inactive*).

### JMS Configuration Page

This page contains the mandatory input arguments that must be provided to establish a JMS connection.

- For the **initial** connection, fill in the settings and then click **Connect**.
- To apply **new settings** to an existing JMS connection, first click the **Disconnect** button, specify the settings, and then click the **Connect** button.

If the JMS connection is cut off intermittently, a retry mechanism is activated to reestablish the JMS connection. Infinite retries can be set for the JMS connection with a minimum interval of 1 s. Use this with caution as this might stress the device.

### Alarms Page

This page contains the list of alarms in the **Alarm Events** table.

With the **Refresh** button on this page, you can retrieve all alarms from the NFM-P main server and refresh the table. However, note that since the volume of the alarms might be high, this can have a performance impact on the system if triggered frequently.

### Debug Page

This page contains useful metrics like buffer counts and logs from the JMS connection. You can configure the number of things taken from the buffers.
