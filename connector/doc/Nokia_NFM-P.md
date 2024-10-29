---
uid: Connector_help_Nokia_NFM-P
---

# Nokia NFM-P

Nokia NFM-P connector is used by Kordia to track the alarm events in the NFM-P network via XML API and JMS subscription. The XML API is an NFM-P interface that provides an XML interface ot the NFM-P through which an OSS client application can retrieve NFM-P network management information, receive event notifications from the NFM-P server using a persistent or non-persistent JMS connection.

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
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization

In addition to the above HTTP settings, All the arguments in the JMS Configuration page has to be provided in a newly created element before pressing the "Connect" button.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector uses SOAP calls to retrieve the device information and JMS connection to receive alarm events.

### General Page
This page displays system related information. The "JMS Connection" parameter shows the connection's status (Active/Inactive).

### JMS Configuration Page
This page contains the mandatory input arguments that must be provided to establish a JMS connection.
- For initial connections, fill in the settings before pressing the "Connect" button.
- To apply new settings to an existing JMS connection, press the "Disconnect" button followed by the "Connect" button.
- If the JMS connection is cut off intermittently, a retry mechanism is activated to reestablish the JMS connection.
- Infinite retries can be set for the JMS connection with a minimum interval of 1s. Use it with caution as this might stress the device.

### Alarms Page
- This page contains the list of alarms in the Alarm Events table.
There is a Refresh button on the same page that can be used to get all alarms on the NFM-P main server and refresh the Alarm Events table.
Note: Since the volume of the alarms might be high, this can have a performance impact on the system, if triggered frequently.

### Debug Page
- This page contains useful metrics like buffer counts and logs from JMS connection.
- The number of things taken out from the buffers are configurable.