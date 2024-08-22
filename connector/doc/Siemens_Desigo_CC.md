---
uid: Connector_help_Siemens_Desigo_CC
---

# Siemens Desigo CC

The connector will subscribe on all the values on the siemens desigo cc system that were provided with an excel file.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |6.0.97.105         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTPS Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTPS CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *8080*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

#### HTTPS Connection - Redundant

This connector uses an HTTP connection and requires the following input during element creation:

HTTPS CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *8080*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Initialization

Fill in the username and password.
Also import an excel file with the parameters that want to be retrieved.

The excel file should have 1 column with the name of the value from on the Siemens Desigo CC system.
The name can be found on the GUI.

## How to use

The values table will be filled in with the values that are being provided through the excel file.
There are subscription so the values should be pushed by the siemens system to dataminer.
