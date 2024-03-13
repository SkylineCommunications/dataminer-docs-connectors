---
uid: Connector_help_beIN_GPIO_Mapping
---
# beIN GPIO Mapping

The beIN GPIO Mapping is a protocol that allows to show Frame PSU State parameters, which are destinations connected to source parameters via Element Connections.

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                     |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

For this element and parameters to show relevant data, you need to connect the 11 parameters (that serve as destinations) with sources. This can be done via **Element Connections**. An element running the protocol *Advantech ADAM5050* could e.g. provide parameters that can serve as sources.

## How to use

In the connector there is 1 page **Frame PSU States** with 11 parameters that can be monitored. Discreet values are preconfigured as *Fault (0)* and *Healthy (1)*. 