---
uid: Connector_help_Verizon_WM_Ticketing
---

# Verizon WM Ticketing

The Verizon WM Ticketing connector is used to handle the Verizon VSAT business logic towards the automation of the ticketing workflow. The connector interacts, directly or indirectly, with collector elements, Correlation rules, and Automation scripts.

## About

As this is a virtual connector, **no data traffic** will be shown **in the Stream Viewer**.

### Enterprise Ticketing Management System (ETMS) Integration

1. The Correlation engine listens for and captures **information events** from collector elements.

1. The Correlation engine triggers an **Automation script**, passing along the ticketing message.

1. The Automation script selects the **Verizon WM Ticketing (WMT) element** responsible for handling the ticketing workflow and forwards the message via a parameter set.

   The WMT element is selected based on the **DMA ID** of the triggering collector. The goal is to process the ticket on the same DMA when possible. If no WMT element is found, the message is sent to any active WMT element within the DMS.

1. The WMT element runs **diagnostic checks** as part of the ticketing workflow, evaluating various conditions affecting the alarmed entity.

   For details on each diagnostic type, refer to [Diagnostics](#diagnostics) below.

1. Once diagnostics are completed, the WMT element sends the final ticketing message to the ETMS back end operating on the current DMA.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version. Uses BinaryFormatter, which contains deserialization and security vulnerabilities and should not be used. | No | Yes |
| 1.0.1.x [Obsolete] | Layout adapted and SLA and fault logic implemented. | No | Yes |
| 1.0.2.x [Obsolete] | Minimum DataMiner required version increased from 10.0.3.0 - 8964 to 10.0.10.0 - 9454. | No | Yes |
| 1.0.3.x [SLC Main]| Starlink alarms support added. | No | Yes |

## Configuration

The **Configuration** section allows you to adjust the behavior of the connector, including ticketing settings, topology imports, and system credentials. The following areas can be configured:

- **Ticketing Settings**: Controls ticket request processing, including enabling/disabling ticketing, setting request limits, and defining timing parameters.

- **SLA & Fault Configuration**: Manages SLA and fault monitoring updates, including enabling updates and configuring update intervals.

- **Ticketing Configuration**: Defines ticketing system integration, specifying the ticketing platform, listeners, and data center settings.

- **Topology Import Settings**: Configures topology imports, including enabling imports, setting directory paths, and defining import intervals.

- **System Credentials**: Stores authentication details for system access.

- **Subscriptions Configuration**: Defines the **front-end DMA** and **subscription file locations**.

- **Subscriptions Folder Path**: The path where **subscription tables** will be stored.

  > [!NOTE]
  > This must be written like a local path but applies to the **front-end Agent**, not the hosting Agent.

## Diagnostics

The **Diagnostics** section provides an overview of automated checks performed by the **Verizon WM Ticketing** connector. Each diagnostic type has its own page, where you can enable or suppress it.

### Available Diagnostics

The connector supports the following diagnostic types:

- **PLM Diagnostic**: Retrieves **PLM activities** from the **Skyline EPM Platform PLM** connector and adds relevant PLM activities to the diagnostic details.
- **Sun Outage Diagnostic**: Checks for **sun outages** affecting the entity using the **Generic Sun Outage** connector.
- **Weather Diagnostic**: Queries **Skyline Universal Weather** for the entity’s location and includes the weather conditions in the diagnostic results.
- **Network Connectivity Diagnostic**: Marks the diagnostic as **Active** if the fault type is **Network Connectivity**.
- **Temperature Diagnostic**: Identifies **temperature-related issues** when the fault type is **Circuit Performance** or **Infrastructure Performance**, using recent temperature-related events.
- **KPI Diagnostic**: Evaluates key performance indicators based on the **KPI Callback Overview** table.
