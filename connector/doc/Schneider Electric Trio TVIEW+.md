---
uid: Connector_help_Schneider Electric Trio TVIEW+
---

# Schneider Electric Trio TVIEW+
The TVIEW+ is a network management and diagnostics software application for Trio™ data radios, providing support for multiple diagnostic hosts, integrated graphical spectrum analysis, and remote radio configuration.

## About

The **Schneider Electric Trio TVIEW+** connector communicates through SNMP and gathers data of the connected radios, including their status, configuration, and performance metrics.
The collected data is then presented in a structured format, allowing for easy monitoring and management of the Trio TVIEW+ environment.

### Version Info

| Range              | Description                  | DCF Integration | Cassandra Compliant |
|--------------------|------------------------------|-----------------|---------------------|
| 1.1.0.x            | Release version              | No              | Yes                 |


## Configuration

### Creation
This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:
SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.
## Usage

### General
This page displays general information about the application such as the Object Identifier, System Up time, System Name, System Location, System Description and System Contact.

#### Configuration
This page allows you to view and edit the datetime configuration of this connector.
You can switch between the local time and UTC time to update date time values in the connector. By default, the connector uses the local time zone.

### Series
This page displays the All Series table. Which is a collection of all the series that are being monitored by this connector.
The table contains the common data found among all the series types, such as the name, frequency error, transmit power forward, location etc.

#### ESeries
This page displays the ESeries table. Which is a collection of all the ESeries data radios that are being monitored by this connector.
This table contains more specific data related to the ESeries data radios as compared to the All Series Table, specificaly the transit power reverse.

### DVE
This page displays the DVE table. Which is a collection of all the DVEs that are currently created.

#### DVE Configuration
This page allows you to view and edit the configuration of the DVEs.
You can set the default view name that will tied to each series. This is the view that the DVE will belong to when created.
You can also set "Delete DVEs on Old Series" to automatic or manual. When set to automatic, the connector will automatically delete the DVEs that are linked to a series that is no longer being monitored by the connector.

##### Series DVE Configuration Table
This table contains the configuration of the DVEs that are linked to each series. It allows you to set the View Name specific to each series, which will override the default view name when creating the DVE for that series.
It also allows you to manually delete the series from the DVE configuration table. However this is only possible when the DVE is disabled, and the series is not being monitored by the connector (No longer present). This means that the DVE is not created, and the series is not present in the All Series table.

### Alarms
This page displays the Alarms table. Which is a collection of all the alarms that are currently active in this connector.
The alarms shown are the latest alarms that has been triggered.
Some alarm codes do not carry alarm values such as "No ACK". In this case, the alarm value will be shown as "N/A".