---
uid: Connector_help_Al_Jazeera_Media_Network_Comms_Manager
---

# Al Jazeera Media Network Comms Manager

The Al Jazeera Media Network Comms Manager is a virtual connector used to manage a group of connections for a PCR. The PCR does not return information, and as such, is controlled virtually through the connector. No communication is required.

The connector displays a table where you can control Instances, OS IDs, and Tally Colors. These three parameters are used to control the PCRs. CSV functionality is also available.

No traffic will be shown in Stream Viewer for this connector.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

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

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### OS Management

You can add rows to the **Tally State Table** with the **Add New Row Instance** parameter. The **instance** needs to have the following format: `PCRxy_OSz`, where `xy` is a number between 01 and 99, and `z` is a number starting from 1.

The **OS IDs** must be unique; however, this is not enforced, so that you can change between 2 IDs already assigned to different PCRs.

On the CSV Management page, you can set the **full path file** to be used as the CSV (a valid full path is required, ending in .csv). It is possible to both **import** a CSV file containing the table configuration and **export** a CSV file of the current table configuration,

## Notes

A Visio drawing will be available for this connector.
