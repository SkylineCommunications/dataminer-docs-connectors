---
uid: Connector_help_Broadpeak_BKS350_Technical
description: Technical reference for the Broadpeak BKS350 connector, covering the SNMP and HTTP connection settings and the data pages available in the element.
---

# Broadpeak BKS350 Technical

## About

The **Broadpeak BKS350** connector monitors a BKS350 packager streamer over SNMP and HTTP. It retrieves general device information, service performance statistics, live streaming status, output and publishing status, and the alarms reported by the device.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

**SNMP CONNECTION**:

- **IP address/host**: The polling IP or URL of the destination.

**SNMP Settings**:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

**HTTP CONNECTION**:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8091*).
- **Bus address**: The bus address of the device (default: *ByPassProxy*). Specify *ByPassProxy* if the proxy server has to be bypassed.

### Initialization

The HTTP sessions authenticate with credentials. To configure these after you have created the element:

1. Go to the **General** page.

1. Click **API Credentials...**.

1. Fill in the **User** and **Password** of the BKS350 REST API.

   A new poll of the Lives Status table will be triggered.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

The **Webpage** page shows the device web interface at `http://[Polling IP]:8091/`.

## How to Use

### General

This page displays the equipment information, such as **Name**, **Description**, **Serial Number**, **Up Time**, **Version**, and **MiB Version**, as well as the **System Status Value** and the status of each individual module of the device.

In the **CSV Files Config** section, you can enrich the Lives Status, Alarms, and Output Status tables with data that is not available on the device:

1. In the **CSV Import Path** box, enter the folder where the CSV file is located.

1. In the **Lives CSV Filename** box, enter the name of the CSV file.

1. Click **Read CSV**.

   The data from the CSV file will be added to the Lives Status, Alarms, and Output Status tables.

> [!NOTE]
> The CSV file must contain at least four columns, in the order Name, Service Name, Region, and Multicast IP, optionally followed by Origin URL and CDN URL.

### Statistics

This page displays the device statistics, with the most recent sample and its **Sample Time UTC** for each entry: **Max Time to Serve by Netzone**, **Average Time to Serve by Netzone**, **HTTP Status Codes**, **Input/Output Bitrate**, and **Bitrate per Service Type and Format**.

### Live

This page displays the number of live services on the device and the **Lives Status Table**, which contains the **Status**, **Live State**, **Input Status**, **Output Status**, bitrate, source URLs, and fragmentation settings of each live service.

In the table, you can select an action in the **Actions** column to pause, resume, or restart a service, switch the **Input Source** between *Main* and *Backup*, and click **Delete** to remove a service.

### Alarm

This page displays the **Alarms Table**, which contains the **Alarm Event Time**, **Severity**, **Description**, and **Service ID** of each alarm reported by the device.

### Output

This page displays the **Output Status** table, which contains the **Live Name**, **Template Name**, **Format**, and **Status** of each output.

### Publishing

This page displays the **Publisher Installation Status**, the number of publishing entries, and the **Publishing Status** table, which contains the **Source Identifier**, **Destination URL**, **Source URL**, **Format**, **Status**, and number of **Elements Pushed** and **Elements Failed**.

## Notes

- When you upgrade from range 1.0.0.x to 1.0.1.x, existing elements need to be reconfigured before the new connection will be taken in use.
- When you upgrade to range 1.0.2.x, alarm and trending history will be lost due to the changed primary key (PK) format.
