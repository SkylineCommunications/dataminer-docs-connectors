---
uid: Connector_help_Generic_Ember+
---

# Generic Ember+

The Ember+ protocol has been designed to allow the communication between two endpoints, one being the data provider and the other one being the consumer. The data provider usually is a piece of hardware which offers a set of controllable parameters, while the consumer may be a control- or monitoring-system which provides access to these parameters and allows controlling them.
The Generic Ember+ connector, which is the consumer, is designed to allow monitoring of parameters that are provided via the Ember+ protocol irrespective of the specific device type.

## About

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |1.8.2.2         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:



- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *9000*)]
  



### Initialization

### Redundancy

There is no redundancy defined.



## How to use

This connector retrieves and presents all the parameters that are available in the Ember+ tree structure of the device.

*You can find all the information you need to monitor on the General data page.*
