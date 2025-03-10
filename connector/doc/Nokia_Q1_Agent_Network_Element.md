---
uid: Connector_help_Nokia_Q1_Agent_Network_Element
---

# Nokia Q1 Agent Network Element

The Nokia node devices of the **Nokia DCNA** system that managed by the **Nokia Q1 Agent**.

This type of Nokia Q1 Agent DVE is a virtual representation of a managed node device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

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

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

The exported element is defined in the **Device Management** table on the *Device Management page of the main element.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector consists of a general page which display the general information of the node edvice and one page with an alarm table. This table can be used to monitor the state of the node device.