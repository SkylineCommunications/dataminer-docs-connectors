---
uid: Connector_help_Nokia_NFM-P
---

# Nokia NFM-P

The Nokia NFM-P connector is used by Kordia to track the alarm events in the NFM-P network via XML API and JMS subscription.

The XML API is an NFM-P interface that provides an XML interface for the NFM-P through which an OSS client application can retrieve NFM-P network management information and receive event notifications from the NFM-P server using a persistent or non-persistent JMS connection.

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

### Server Alarm Page

This page contains the list of alarms related the NFM-P server itself.

The **Network Alarm Filter File Path** parameter allows you to provide a CSV file for filtering the server alarms. If the alarm name in an incoming alarm exists in the CSV file, it will be added to the server alarm table. Otherwise, it will be added to **Network Alarm** table.

### Network Alarm Page

This page displays the network alarms, filtered from the server alarms.

### Debug Page

This page contains useful metrics like buffer counts and logs from the JMS connection. You can configure the number of things taken from the buffers.
