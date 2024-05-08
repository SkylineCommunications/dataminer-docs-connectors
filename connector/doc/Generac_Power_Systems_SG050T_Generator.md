---
uid: Connector_help_Generac_Power_Systems_SG050T_Generator
---

# Generac Power Systems SG050T Generator

This connector monitors the engine and generator parameters of the SG050T generator.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.21.4             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Modbus Communication

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600* (default: *9600*).
  - **Databits**: Databits specified in the manual of the device, e.g. *7* (default: *8*).
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1* (default: *1*).
  - **Parity**: Parity specified in the manual of the device, e.g. *No* (default: *even*).
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No*.

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.
  - **Bus address**: The bus address of the device (default: *1*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector has two pages, containing only read-only parameters:

- **General**: Displays the engine information.
- **Generator Info**: Displays the generator information.
