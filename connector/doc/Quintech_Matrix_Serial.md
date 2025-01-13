---
uid: Connector_help_Quintech_Matrix_Serial
---

# Quintech Matrix Serial

This connector allows you to view and control the Quintech matrix crosspoints.

This connector uses a serial connection to display information on a Quintech matrix and allows you to configure the matrix.

## About

### Version Info

| Range              | Key Features              | Based on | System Impact |
|--------------------|---------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version           | -        | -             |
| 2.0.0.1 [SLC Main] | Matrix helper implemented | 1.0.0.10 | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 9.34                   |
| 2.0.0.x   | 9.34                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

Serial CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *172.19.19.30*.
- **IP port**: The polling IP port (default: *9100*).
- **Bus Address**: Default: *ff* (version 1.0.0.6).

## How to use

On the **General** page of this connector, you can find **system information** and a page button to the **Ethernet** subpage, where you can configure all connection-related parameters.

On the **Matrix** page, the serial matrix is displayed. You can set a crosspoint between an input and output there. It is also possible to lock or unlock an input or output to prevent incorrect crosspoint sets.

## Notes

The Quintech matrix only allows labels of at most 7 alphanumeric characters.

When you change the label with invalid data in DataMiner Cube:

1. The Cube matrix will show the invalid data.
1. An attempt will be made to change the label on the Quintech matrix using a formatted value, e.g. limited to 7 characters.
1. After the attempt, the label in Cube will be replaced with the data available in the Quintech matrix.

In the 2.0.0.1 range of the connector, the "Matrix helper" has been implemented, which solves issues with locking and setting crosspoints that some users encountered in the previous range.
