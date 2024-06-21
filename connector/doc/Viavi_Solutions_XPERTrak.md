---
uid: Connector_help_Viavi_Solutions_XPERTrak
---

# Viavi Solutions XPERTrak

The **Viavi Solutions XPERTrak** is is a Spectrum Analyzer connector. It polls the data from the RCIs and displayes desired trace from the Upstreamports list.

## About

This connector will initially poll the data for RCI, upon which will poll the data from the ports from that RCI. Each port can be selected and it's trace will be requested from the API which will be shown on the list. Also, a page containing data about the RCI is available.

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

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

Credentials needed for system authentication are needed. Username nad password can be put in on the configuration page.

## How to use

After initial driver authentication and authorization, driver will poll the list of all available RCIs. Selected RCI can be changed on the configuration page. From the selected RCI, all available ports will be requested and they will be presented on General page in the Upstreamports table.
Each port can be individually opened and the trace from that port will be requested and shown on Spectrum Analyzer page.

On the status parameter on the General page, status of the polling is shown, and can be tracked real-time.