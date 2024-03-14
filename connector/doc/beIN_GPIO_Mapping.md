---
uid: Connector_help_beIN_GPIO_Mapping
---
# beIN GPIO Mapping

With the beIN GPIO Mapping connector, you can view Frame PSU State parameters, which are destinations connected to source parameters via [DataMiner Element Connections](https://aka.dataminer.services/virtual-elements-used-for-element-connections).

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
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

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

For this element and parameters to show relevant data, you need to connect the 11 parameters (which serve as destinations) with sources. This can be done via [Element Connections](https://aka.dataminer.services/virtual-elements-used-for-element-connections). An element running the protocol *Advantech ADAM5050* could e.g. provide parameters that can serve as sources.

## How to use

The connector has one data page, **Frame PSU States**, with 11 parameters that can be monitored. Discrete values are preconfigured as *Fault (0)* and *Healthy (1)*.
