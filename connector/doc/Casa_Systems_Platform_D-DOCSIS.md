---
uid: Connector_help_Casa_Systems_Platform_D-DOCSIS
---

# Casa Systems Platform D-DOCSIS

The Casa is designed to support distributed-access architectures, remote PHY, DOCSIS 3.0 and 3.1, all video types, and software-defined networking. This connector allows you to collect all the data within the Casa device. This data is then centralized within the connector and used by DataMiner EPM for aggregation actions.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 16.12.1z               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. **Default port: 161.**
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### Serial Connection - CLI Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. **Default port: 22.**
  - **Bus address**: The bus address of the device.

#### Serial Connection - NetConf Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. **Default port: 830.**
  - **Bus address**: The bus address of the device.

### Initialization

Once you have created the element, on the **Configuration** page, enter the **CLI/Serial credentials** so the CLI polling can work properly. Once this is done, the element will start regular polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

When you first start using this element, navigate to the Configuration page and enter the credentials for the CLI Interface in the CLI Credentials section. This will allow data retrieval from the CLI endpoint to begin. A number of configuration options are available that can change the behavior of the connector.

- **Interface Settings**: Allows you to enable or disable polling from an interface (SNMP, CLI) via a toggle button. You can also specify how frequently the interface should be polled. This section also contains the following buttons:

- **Update All:** Polls from both interfaces and the virtual interface afterwards.
  - **Update SNMP**: Polls from SNMP only.
  - **Update CLI**: Polls from CLI only.
  - **Update Virtual:** Polls the necessary data from the other interfaces for DCF and EPM connections.

- **Entity Export/Import Settings**: These sections allow the exporting of configuration files and importing of provisioning files. You can:

- **Enable or disable** the exporting and importing feature with toggle buttons (Entity Export and Entity Import, respectively).
  - Specify the **file paths** where files can be exported and imported (with the Entity Export Directory and Entity Import Directory, respectively).
  - Specify whether to export/import to/from a **local or remote** location via a toggle button (Entity Export Directory Type and Entity Import Directory Type, respectively). Note that for the remote file handling to work, you must enter the credentials for the system in the System Credentials section and enter the path to the remote directory in the Entity Export or Import Directory parameter. The path must be shared/accessible, or this feature will not work.
  - Start the export or import by clicking the **Apply** button in the relevant section.

## Notes

This connector requires specific Correlation rules and Automation scripts for communication with EPM connectors such as Skyline CCAP Platform EPM and Skyline CCAP Platform WM. The Correlation rules and Automation scripts must be configured and enabled in order to get the full functionality of this connector.

With larger devices/large data sets the polling performance may vary. You can control the number of rows and cells requested for larger tables by navigating to the Configuration page and enabling debug in the other settings section. This will make the debug page visible, where you can then change SNMP Cell Amount and SNMP Row Amount to a value that works optimally for your system. Increasing these values can cause polling issues such as RTEs and missing data, so be careful and always double-check to make sure the system is stable.

## DataMiner Connectivity Framework

The **1.0.0.x** range of the CISCO CBR-8 CCAP Platform Collector protocol supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Dynamic interfaces

Physical dynamic interfaces:

- DCF interfaces are generated from interfaces with speeds above 10 Mbps.
