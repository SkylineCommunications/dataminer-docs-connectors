---
uid: Connector_help_Warner_Bros_Discovery_Sports_Transmission_Orders
---

# Warner Bros Discovery Sports Transmission Orders

The Warner Bros Discovery Sports Transmission Orders connector can be used to parse and display the sports transmission orders pushed through the **Warner Bros Discovery Transmission Orders** user-defined API.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 10.1.0.0           |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                      | Exported Components |
|---------|-----------------|---------------------|--------------------------------------------------------|---------------------|
| 1.0.0.x | No              | Yes                 | Warner Bros Discovery Transmission Orders API Endpoint |                     |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

This connector parses transmission order JSON requests received from the Warner Bros Discovery Transmission Orders API Endpoint. No communication will therefore be shown in the Stream Viewer.

This connector has a hidden **DEBUG** page. To display this page, execute a multiple set on the **Show Debug Page** parameter.

A high-level overview of the transmission orders can be found on the **Transmission Orders page**.

Each transmission order can have one or multiple services. These are aggregated and displayed on the **Services page**.

In case a service has facilities or audio, these will be displayed on the **Facilities** or **Audio's page**, respectively.

On the **Overview Page**, you can find a tree control displaying these relations.
