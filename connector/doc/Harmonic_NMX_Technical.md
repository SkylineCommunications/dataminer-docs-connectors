---
uid: Connector_help_Harmonic_NMX_Technical
---

# Harmonic NMX

## About

Harmonic's NMX Digital Service Manager is a video network management solution, encompassing a set of tools to monitor and manage Harmonic compressed digital video and audio systems.

The connector communicates with the NMX system using different protocols depending on the range:

- Serial (XML SAPI) for older ranges 1.0.0.x - 4.0.0.x
- HTTP REST API with WebSocket notifications for newer ranges 4.1.0.x and later

## Exported Dynamic Virtual Elements

The connector supports the following types:

- [Harmonic NMX - Device](xref:Connector_help_Harmonic_NMX_-_Device)
- [Harmonic NMX - Switch](xref:Connector_help_Harmonic_NMX_-_Switch)

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

### Connections - Range 4.2.0.x - 4.3.0.x

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

#### WebSocket Connection

This connector uses a WebSocket connection and requires the following input during element creation:

WEBSOCKET CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

> [!NOTE]
> In the **IP address/host** field, you must specify the **prefix *ws://* or *wss://***, depending on whether an HTTP or HTTPS connection is used.

### Initialization - Range 4.1.0.x - 4.1.1.x and 4.2.0.x - 4.3.0.x

In order to start polling data from the device, go to the **General** page of the element and fill in the **Username** and **Password** (and optionally the **Domain**). If you have filled in the correct credentials, the **Login Status** will be set to *OK*, and the data in the element will be filled in.

We advise the use of a dedicated API user to manage this connection.

## How to Use

Depending on the connector range, the element created with this connector can have the data pages detailed below.

### General Page

The General page displays an overview of all general parameters.

On the left-hand side, you can find the **Alarm Server Version**, the **ID of the last alarm**, the maximal **number of alarm entries**, and a toggle button to change the **trap state of the AFA mode**.

On the right-hand side, the primary and backup **IP addresses** and the **Redundancy Status** are displayed, as well as the **Poll SAPI Interface** parameter, which can be used to enable or disable the polling of serial commands. The latter is used for a redundancy feature in this connector that allows dynamic polling between primary and backup IP addresses to keep track of socket errors in SAPI registration processes in slow or fast serial connections.

### Alarm Page

The Alarm page displays all active alarms on the system.

> [!NOTE]
> From version 4.1.1.7 onwards, you can change the Alarm table display key by selecting your preference in the **Alarm Display Key** box. **Changing this value will affect your Alarm Console descriptions and may affect historical element data** (alarm and trending).

### Ports Page

The **Ports** table allows you to enable or disable individual input and output ports within the Harmonic NMX element.

Each port entry in the table includes an **Enable/Disable** setting:

- When a port is **enabled**, the element will display the corresponding information in both the **Input** and **Output** sections.
- When a port is **disabled**, it will be excluded from processing, and the element will **not display any data** for the port in the Input and Output sections.

> [!NOTE]
> If **all ports are disabled**, no data will be shown in the Input or Output sections of the element.

### Platform Page

The Platform page contains parameters related to the creation of the different DVEs and a global overview of all available devices.

The **DVE Automatic Deletion** toggle button can be set to *Enabled* to have DVEs removed automatically when the corresponding device is no longer found. If this button is set to *Disabled*, the **DVE Status** in the **DVE Manager** table will be set to *Not Detected* for devices that are no longer found. You can then remove these DVEs manually using the **Delete DVE** button.

You can also configure the DVE child's name and the view where it should be located, using the **DVE Name** and **DVE View** columns in the **DVE Manager** table.

> [!NOTE]
> Enabling autoclear has an important downside. If a device disappears from the system for a short time, the DVE will be deleted. If the device reappears later, a new DVE will be created. However, if a Visio drawing is made based on the element ID of the DVE, this drawing will not display the new DVE.

### WebSocket Notifications

Available from range 4.2.0.x onwards. The **General** page displays the current status of the WebSocket connection.

The WebSocket connection handles notifications received from the device. The following notifications are currently received and processed:

- **ObjectModifiedNotification**: Receives the service plan attached to the modified object and sends a request for the service plan.
- **ObjectCreatedNotification**: Receives the service plan attached to the created object and sends a request for the service plan.
- **ObjectDeletedNotification**: Removes the deleted data.
- **Alarms**: Updates the Alarms Table to either remove or add an alarm.

> [!NOTE]
> The ObjectModifiedNotification/ObjectCreatedNotification service plan request is only sent if **Poll Service Plan Details** is enabled on the Service Plan page.

## Notes

As ranges 4.1.0.x/4.1.1.x, 4.2.0.x, and 4.3.0.x use the REST API introduced in firmware 8, there are some parameters and metrics that are not available compared to previous ranges, where the connector communication used the XML SAPI.
