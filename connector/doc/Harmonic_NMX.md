---
uid: Connector_help_Harmonic_NMX
---

# Harmonic NMX

Harmonic's NMX Digital Service Manager is a video network management solution, encompassing a set of tools to monitor and manage Harmonic compressed digital video and audio systems.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version. | - | - |
| 2.0.0.x | Initial version SNMP. | - | - |
| 3.0.0.x | DVE integration. | - | - |
| 4.0.0.x | Parsing XML with LINQ, streams per device. | - | - |
| 4.0.1.x | Smart-serial conversion. | - | - |
| 4.1.0.x [Obsolete] | REST API communication. | 4.0.1.5 | - |
| 4.1.1.x [Obsolete] | - REST API refactored. <br>- Enhancement of HTTP data relations and organization. | 4.1.0.3 | - Primary/display keys changed. <br>- Possible impact on monitoring and trending. |
| 4.2.0.x [SLC Main] | Added WebSocket connection. New firmware version support. Possible to select regular HTTP polling or WebSocket communication. | 4.1.1.22 | If you use a range supporting firmware 8, you will need to configure the new WebSocket connection. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Unknown                |
| 2.0.0.x   | Unknown                |
| 3.0.0.x   | Unknown                |
| 4.0.0.x   | Unknown                |
| 4.0.1.x   | 6.4                    |
| 4.1.0.x   | 8                      |
| 4.1.1.x   | 8                      |
| 4.2.0.x   | 9.13, 9.2, 8           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components                              |
|-----------|---------------------|-------------------------|-----------------------|--------------------------------------------------|
| 1.0.0.x   | No                  | No                      | -                     | -                                                |
| 2.0.0.x   | No                  | No                      | -                     | -                                                |
| 3.0.0.x   | No                  | No                      | -                     | -                                                |
| 4.0.0.x   | No                  | No                      | -                     | -                                                |
| 4.0.1.x   | No                  | No                      | -                     | -                                                |
| 4.1.0.x   | No                  | Yes                     | -                     | - Harmonic NMX - Device                         |
| 4.1.1.x   | No                  | Yes                     | -                     | - Harmonic NMX - Device <br>- Harmonic NMX - Switch |
| 4.2.0.x   | No                  | Yes                     | -                     | - Harmonic NMX - Device <br>- Harmonic NMX - Switch |

## Configuration

### Connections - Range 1.0.0.x - 4.0.0.x

#### Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Timeout Time**: 30000 ms.
  - **Retries**: 3.

- Interface connection:

  - **IP address/host**: The polling IP of the device or, if redundancy mode is permitted, the primary/backup IP.
  - **IP port**: 9001.
  - **Bus Address**: NA.

#### Serial Connection - SerialSlowConnection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Timeout Time**: 30000 ms.
  - **Retries**: 1.

- Interface connection:

  - **IP address/host**: The polling IP of the device or, if redundancy mode is permitted, the primary/backup IP.
  - **IP port**: 9001.
  - **Bus Address**: NA.

#### SNMP Connection - snmp

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device or, if redundancy mode is permitted, the primary/backup IP.

SNMP Settings:

- **IP port**: 161
- **Get community string**: public
- **Set community string**: private

### Connections - Range 4.0.1.x

#### Smart-Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Timeout Time**: 5000 ms.
  - **Retries**: 3.

- Interface connection:

  - **IP address/host**: The polling IP of the device or, if redundancy mode is permitted, the primary/backup IP.
  - **IP port**: 9001.
  - **Bus Address**: NA.

#### SNMP Connection - snmp

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device or, if redundancy mode is permitted, the primary/backup IP.

SNMP Settings:

- **IP port**: 161
- **Get community string**: public
- **Set community string**: private

### Connections - Range 4.1.0.x - 4.1.1.x

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Connections - Range 4.2.0.x

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

#### WebSocket Connection

This connector uses a WebSocket connection and requires the following input during element creation:

WEBSOCKET CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

> [!NOTE]
> In the **IP address/host** field, you must specify the **prefix *ws://* or *wss://***, depending on whether an HTTP or HTTPS connection is used.

### Initialization - range 4.1.0.x - 4.1.1.x and 4.2.0.x

In order to start polling data from the device, go to the **General** page of the element and fill in the **Username** and **Password** (and optionally the **Domain**). If you have filled in the correct credentials, the **Login Status** will be set to *OK*, and the data in the element will be filled in. We advise the use of a dedicated API user to manage this connection.

## How to use

Depending on the connector range, the element created with this connector can have the data pages detailed below.

### General Page

The General page displays an overview of all general parameters.

On the left-hand side, you can find the **Alarm Server Version**, the **ID of the last alarm**, the maximal **number of alarm entries**, and a toggle button to change the **trap state of the AFA mode**.

On the right-hand side, the primary and backup **IP addresses** and the **Redundancy Status** are displayed, as well as the **Poll SAPI Interface** parameter, which can be used to enable or disable the polling of serial commands. The latter is used for a redundancy feature in this connector that allows dynamic polling between primary and backup IP addresses to keep track of socket errors in SAPI registration processes in slow or fast serial connections.

### Alarm Page

The Alarm page displays the alarms that come in through SNMP polling and traps.

It contains the following page buttons:

- **Filters**: Displays a table that allows you to filter the alarm table and count how many **occurrences of an alarm** are present. The filter is applied on the column **Info String** of the alarm table. To add a filter, click **Add Row** and fill in the filter in the added row. The filter should be a string, optionally containing a wildcard (\*).
- **Trap Config**: Allows you to configure which IP traps should be taken into account using the **Accept Traps From** parameter. The parameter value can be a single IP address or a comma-separated list of IP addresses. The addresses can contain "\*" and "?" wildcards.

From version 4.1.1.7 onwards, you can change the Alarm table display key by selecting your preference in the **Alarm Display Key** box. However, note that **changing this value will affect your Alarm Console descriptions and may affect historical element data** (alarm and trending).

### Ports Table

The **Ports** table allows users to enable or disable individual input and output ports within the Harmonic NMX element.

Each port entry in the table includes an **Enable/Disable** setting:

- When a port is **enabled**, the element will display the corresponding information in both the **Input** and **Output** sections.
- When a port is **disabled**, it will be excluded from processing, and the element will **not display any data** for the port in the Input and Output sections.

> [!NOTE]
> If **all ports are disabled**, no data will be shown in the Input or Output sections of the element.

### Device Service Page

The Device Service page displays an overview of **all services per device**.

Prior to range 4.0.1.x, it contains a page button, **Data Tables**, that displays internal parameters that are exported to the DVEs. This page button must be displayed to enable the correct functioning of the DVEs but is **not intended for use by an operator**.

From range 4.0.1.x onwards, it contains the below-mentioned page buttons with internal parameters that are exported to the DVEs. These page buttons must be displayed by design to enable the correct functioning of the DVEs but are **not intended for use by an operator**:

- **Stream Types**: Displays information on the device stream types.
- **Stream Queries**: Displays information on the stream path query.
- **Input Audio PID**: Displays information on the input audio PID.
- **Input Service**: Displays information on the input services.
- **Input Other PID**: Displays information on other input PIDs.
- **Input Video PID**: Displays information on the descriptor input video PIDs.
- **Output Stream Descriptor**: Displays information on the descriptor output streams.
- **Output PID**: Displays information on the output PIDs.
- **Output Service**: Displays information on the output services.
- **Output Stream**: Displays information on the output streams.
- **Redundancy Group**: Displays information on the redundancy group.
- **Stream Overview**: Displays a tree control containing the streams (inputs/outputs).
- **Matrix**: Displays matrix information on the devices.
- **Port**: Displays information on the ports.
- **Redundancy Switches**: Displays information on the redundancy switches, including how they are linked. Also allows you to switch between devices.

### Redundancy Overview Page

The Redundancy Overview page displays a tree control, showing the **primary and backup devices per redundancy group**. The tree control also indicates if a backup took over from a primary device. However, note that the redundancy parameters only display the correct values if the **IsBackup** property is correctly defined on the Harmonic element.

### Platform Page

The Platform page contains parameters related to the creation of the different DVEs.

In the **Platform Table**, the **System Uptime** is polled per device. By default, the same SNMP get community string is used for the DVE children as for the parent DVE element. To define a different community string per device, fill in a value in the **Overwrite SNMP Community** column in this table.

The **Autoclear Platform** toggle button can be set to *Enabled* to have DVEs removed automatically when the corresponding device is no longer found. If this button is set to *Disabled*, in the row corresponding to the device, the column **Missing Platform** will instead be set to *Yes*, and you can then remove the DVE manually by clicking the button **Remove Missing**.

Note: Enabling autoclear has an important downside. If a device disappears from the system for a short time, the DVE will be deleted. If the device reappears later, a new DVE will be created. However, if a Visio drawing is made based on the element ID of the DVE, this drawing will not display the new DVE.

This page also contains the following page buttons:

- **Extra Poll**: Displays a table with the platform types that require extra polling to detect **input stream redundancy socket switching** sooner.

  To add a row to this table, fill in a platform type in the **Add Extra Poll Platform Type** parameter and click the **Add** button. To remove a row, use the **Remove** button in the table.

  Note: This generates extra traffic, so we recommend that you add as few platform types as possible.

- **Exclude DVE**: Displays a table with the platform types that should be **excluded from the Platform Table**, i.e. the platform types for which no DVE should be created. By default, the values "INPUT_DEVICE" and "OUTPUT_DEVICE" are filled in. Adding and removing rows in this table is done in the same way as for the Extra Poll Table.

For **range 4.1.0.x - 4.1.1.x** only: For DVEs, it is possible to configure whether child elements should be deleted automatically when they are no longer present in the Harmonic NMX. To do so, configure the **DVE Automatic Deletion** parameter on the **Platform** page. You can also configure the DVE child's name and the view where it should be located, using the **DVE Name** and **DVE View** columns in the **Devices** table.

### WebSocket Connection

The **General** page displays the current status of the WebSocket connection.

The WebSocket connection handles notifications received from the device. The following notifications are currently received and processed:

- **ObjectModifiedNotification**: Receives the service plan attached to the modified object and sends a request for the service plan.
- **ObjectCreatedNotification**: Receives the service plan attached to the created object and sends a request for the service plan.
- **ObjectDeletedNotification**: Removes the deleted data.
- **Alarms**: Updates the Alarms Table to either remove or add an alarm.

The ObjectModifiedNotification/ObjectCreatedNotification service plan request is only sent if **Poll Service Plan Details** is enabled on the Service Plan page

## Notes

As range 4.1.0.x/4.1.1.x and 4.2.0.x use the REST API introduced in firmware 8, there are some parameters and metrics that are not available compared to previous ranges, where the connector communication used the XML SAPI.
