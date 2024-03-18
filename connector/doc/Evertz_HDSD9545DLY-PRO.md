# Evertz HDSD9545DLY-PRO

The Evertz® HDSD9545DLY-PRO is time shifting delay processor with two program paths 
which are HD and SD compatible.
## About

### Version Info

|Range  |Key Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x[SLC Main]|Initial version.|-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |Yes       |Yes         |-         |-   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Port number**: [The port of the connected device. (default: *161*)]
- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

## How to use

The element created with this connector will have 5 data pages. The **General** page includes card type, HDSD9545DLY-PRO or HDSD9545DLY-PRO-HD40.
Next to this, there is a **Control Parameters** page, where general device video/audio parameters, like [Video Standard, Delays, GPI, etc.] can be configured.
Following two pages **Transition Control** and **Output Control** info and configurable data listed in table, regarding sources or outputs.
**Fault Management** lists the fault statuses indexed by fault name and by input index and can be used to configure sending traps in certain situations.