---
uid: Connector_help_Telenor_Cisco_CBR-8_Video_Platform
---

# Telenor Cisco CBR-8 Video Platform

This connector will retrieve Data from an external DMA cluster using Dataminer Web Services and replicate the informaiton in it's own tables. This is to prevent double polling information from the same Cisco CBR-8 device.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

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

  - **IP address/host**: The polling IP or URL of the destination. This will be the address of a DMA from the external DMS cluster.
  - **IP port**: The IP port of the destination. (default: *443*). Change to 80 if external DMS does not have HTTPS configured.
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization

After creating the element, navigate to the **Configuration** page to set up the required API parameters to connect to the external DMS.

All parameters in the **API Configuration** section of this page are required.

  - **API Username** - username with access to the external DMS.

  - **API Password** - Password for the user to log on to the external DMS.

  - **API DMA ID** - DMA ID of Cisco CBR-8 element from external DMS.

  - **API Element ID** - Element ID of Cisco CBR-8 element from external DMS.

On the other pages are the tables that will be retrieved. Above all the tables is a parameter to denote what the Table Parameter ID to be requested to fill in the table. By default, this will already be correctly configured to map to the correct tables using the *Cisco CBR-8 CCAP Platform* driver. If the external DMS is polling the CBR-8 devices with a different driver, these values will need to be updated.

### Redundancy

There is no redundancy defined.



## How to use

The element will request all table data on an interval determined by the **Polling Frequency** parameter in the **Configuration** page. By default this is 15 minutes and can be adjusted accordingly. You can also force to poll the information by pressing the *Poll Now* button on the **General** page.
