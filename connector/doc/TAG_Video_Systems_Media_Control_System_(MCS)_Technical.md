---
uid: Connector_help_TAG_Video_Systems_Media_Control_System_MCS_Technical
---

# TAG Video Systems Media Control System (MCS)

## About

This is an HTTP-based connector that can be used to monitor and configure the **TAG Media Control System Platform**.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Initialization

Specify the following input configuration on the **Communication** page of the element:

- **Username**: Name of the user used in the HTTP login operation.
- **Password**: Password of the user used in the HTTP login operation.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

REST API calls are used to establish communication with the device. For each API request frequency, the version can be adjusted on the **Polling Configuration** subpage of the Communication page.

The **Page Configuration** page allows you to display two useful debugging pages:

- **Tag Sets**: Displays two tables showing changes made to existing data that are in progress or complete.
- **InterApp**: Displays external communication (e.g. from Automation scripts) towards the MCS element.

For several of the tables, you can right-click the table to access a context menu that allows data manipulation and changes.

## Notes

SNMP traps are received via a hidden connection using port 162 in order to automatically update the Channel Events with trap information.
