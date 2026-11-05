---
uid: Connector_help_Telenor_Cisco_CBR-8_Video_Platform
---

# Telenor Cisco CBR-8 Video Platform

This connector will retrieve data from an external DMA cluster using DataMiner Web Services and replicate the information in its own tables. This prevents double polling of information from the same Cisco CBR-8 device.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. This will be the address of a DMA from an external DMS cluster.
- **IP port**: The IP port of the destination. Default: *443*. Change this to *80* if the external DMS does not have HTTPS configured.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After creating the element, navigate to the **Configuration** page to set up the required API parameters to connect to the external DMS.

All parameters in the **API Configuration** section of this page must be filled in.

- **API Username**: Username with access to the external DMS.
- **API Password**: Password for the user to log on to the external DMS.
- **API DMA ID**: DMA ID of Cisco CBR-8 element from external DMS.
- **API Element ID**: Element ID of Cisco CBR-8 element from external DMS.

The other pages contain the tables that will be retrieved. Above the tables, there is a parameter that can be used to set the table parameter ID of each table for which data needs to be retrieved. By default, this will already be correctly configured to map to the correct tables using the Cisco CBR-8 CCAP Platform connector. If the external DMS is polling the CBR-8 devices with a different connector, the table parameter ID values will need to be updated.

## How to use

The element will request all table data on an interval determined by the **Polling Frequency** parameter on the **Configuration** page. By default, this is 15 minutes, but you can customize this. You can also force the polling of the information by clicking the **Poll Now** button on the **General** page.
