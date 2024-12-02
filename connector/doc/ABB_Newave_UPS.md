---
uid: Connector_help_ABB_Newave_UPS
---

# ABB Newave UPS

The connector allows you to monitor and configure the ABB Newave UPS through the USHA+ interface, which obtains the status from a UPS and issues commands to it.

USHA+ supports HTTP and SNMP protocols.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

SNMP is used to retrieve the device information. On element creation, IP address of the device must be set.
To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting View \> Stream Viewer.
Pages section describes what data each page contains.

## Pages

### General

This page contains general information about the UPS, such as the name, manufacturer, model, etc.

### UPS Unit Summary

This page contains information about the UPS battery, such as **Battery Status**, **Battery Runtime Remaining**, **Battery Temperature**, etc.

On the subpages, more information is available on the UPS battery, output, and input.

### UPS Global Configuration

This page allows you to configure various settings for the UPS, such as the **UPS Input voltage**, **UPS Input Frequency**, etc.

### Global UPS Shutdown Control

On this page, you can configure the shutdown settings: **UPS Shutdown Type**, **UPS Shutdown After Delay**, **UPS Auto Restart**, etc.

### UPS Battery Test

This page shows battery test information, such as **UPS Test Results Summary**, **UPS Test Start Time**, **UPS Test Elapsed Time**, etc.

### UPS Bypass

This page shows the **UPS Bypass Frequency**, **UPS Bypass Table**, and **UPS Bypass Number of Lines**.

### Global Alarm Table

This page shows the number of alarms present, as well as a table with additional details for each alarm.
