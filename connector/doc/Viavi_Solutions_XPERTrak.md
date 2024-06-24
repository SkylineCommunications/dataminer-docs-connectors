---
uid: Connector_help_Viavi_Solutions_XPERTrak
---

# Viavi Solutions XPERTrak

The Viavi Solutions XPERTrak is a Spectrum Analyzer connector. It polls data from the RCIs and allows you to view a specific trace from the upstream ports.

This connector will initially poll the data for an RCI, upon which it will poll the data from the ports from that RCI. Each port can be selected, and its trace will be requested from the API that will be shown in the list. A page with data about the RCI is also available.

## About

### Version Info

| Range              | Features        | Based on | System Impact  |
|--------------------|-----------------|----------|----------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -              |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration  | Cassandra Compliant  | Linked Components | Exported Components   |
|---------|------------------|----------------------|-------------------|-----------------------|
| 1.0.0.x | No               |Yes                   | -                 |                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When you have created the element, on the **Configuration** page, fill in the **Username** and **Password** required for system authentication.

## How to use

After the initial connector authentication and authorization, the connector will poll the list of all available RCIs. On the **Configuration** page, you can change which RCI is selected.

All available ports will be requested from the selected RCI, and they will be displayed on the **General** page in the **Upstreamports** table.

You can open each port individually. The trace from that port will be requested and shown on the **Spectrum Analyzer** page.

On the **General** page, the status parameter shows the status of the polling and allows you to track this in real time.
