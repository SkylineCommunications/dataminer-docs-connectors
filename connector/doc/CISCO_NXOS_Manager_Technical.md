---
uid: Connector_help_CISCO_NXOS_Manager_Technical
---

# CISCO NXOS Manager

## About

CISCO NXOS Manager Connector interfaces with Cisco Nexus switches to collect network state and configuration using the OpenConfig data models and gNMI. It enables standardized, vendor-agnostic telemetry and automation for real-time monitoring and network operations.

> [!IMPORTANT]
> When gNMI is used to retrieve device information:
>
> - The Communication Gateway DxM must be installed on the DataMiner Agent (DMA).
> - Configure the connector to run with its own **SLProtocol** and **SLScripting** processes (see [Configuring separate SLProtocol and SLScripting instances for a specific protocol](https://aka.dataminer.services/configuring-separate-slprotocol-and-slscripting-instances)).
> - Limit the number of elements for one DataMiner Agent to approximately 60.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

#### Configuration of credentials for gNMI communication

On the **Element Settings** page, fill in the **gNMI Settings** and click **Connect** to establish the gNMI communication.

Make sure to fill in the full address in the **gNMI IP Address** e.g. https://x.x.x.x , the **Client Certificate** parameter is optional.

## How to use

### Communication Settings

On the **Communication Manager** page under the **Element Settings**, you can configure how data is retrieved. This table is only visible to users with Level 4 permissions.

Following configurations can be made to retrieve the underlying data paths:

- **Type: Poll** — Requires an interval to be specified. The connector will poll the data source at the defined interval.
- **Type: Subscribe with Interval** — Creates a Sampled subscription. The target system sends data updates once per specified interval. This method is commonly used for counters.
- **Type: Subscribe with Interval 0** or **Type: Subscribe (On Change)** — Creates an On Change subscription. The connector receives data updates only when the value of a data item changes.

> [!NOTE]
> - It is recommended to keep the default settings, as they are carefully optimized to ensure the best performance when retrieving data between the data source and DataMiner.
> - Data retrieved using these settings is **not** visible in the **Stream Viewer**.


### Examples

*On the **System** page of this connector, you'll find key system parameters, including CPU usage and process details.*

*In the **Platform** section, you’ll find dedicated pages for **PSU**, **Fan**, and **Temperature** monitoring, providing insight into the system’s hardware components.*

*The **Interfaces** section provides general interface details, performance counters, and transceiver information for comprehensive network port monitoring.*

*The **LLDP** page displays how devices are interconnected across the network.*

## Dataminer Connectivity Framework

The **1.0.0.x** range of the CISCO NXOS Manager connector supports the usage of DCF.

**DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).**

### Interfaces

#### Dynamic interfaces

Physical dynamic interfaces:

- **Interfaces:** Physical interfaces, type **inout** (in/out/inout).