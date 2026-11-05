---
uid: Connector_help_Newtec_Dialog_Inventory_Technical
---

# Newtec Dialog Inventory

## About

The Newtec Dialog Inventory connector collects, organizes, and presents configuration data from the infrastructure that supports the Newtec Dialog VSAT Platform. It is originally based on the Newtec Dialog Infrastructure connector.

The connector interacts with the Newtec Dialog Platform and external NMS systems of type **4IF**, **XIF**, or **NIF** via **DataMiner Web Services**, enhancing its visibility into the platform's infrastructure and supporting centralized inventory management.

It retrieves and aggregates system component data such as modulators, demodulators, switches, servers, and virtual machines, and displays the data using a **tree control** structure to represent the hierarchy of each Configuration Item type (or "CI Type") within the respective NMS.

It also exports the following **DVEs**:

- [Newtec Dialog Inventory - M6100 Modulator](xref:Connector_help_Newtec_Dialog_Inventory_-_M6100_Modulator)
- [Newtec Dialog Inventory - MCM7500 Modulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCM7500_Modulator)
- [Newtec Dialog Inventory - MCD6000 Demodulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCD6000_Demodulator)
- [Newtec Dialog Inventory - MCD HRC Demodulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCD_HRC_Demodulator)
- [Newtec Dialog Inventory - MCD MRC Demodulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCD_MRC_Demodulator)
- [Newtec Dialog Inventory - MCD 4CPM Demodulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCD_4CPM_Demodulator)
- [Newtec Dialog Inventory - MCD7000 Demodulator](xref:Connector_help_Newtec_Dialog_Inventory_-_MCD7000_Demodulator)
- [Newtec Dialog Inventory - PTP Sync](xref:Connector_help_Newtec_Dialog_Inventory_-_PTP_Sync)

## Configuration

### Connections

#### HTTP Connection - 1

This connector uses an HTTP connection to access both the Dialog Platform and external NMSs. The following details are required during element creation:

- **IP address/host**: IP of the Newtec Central NMS.
- **IP port**: *80*
- **Device address**: *BypassProxy*

### Initialization

After element creation, navigate to the **General** page to configure **credentials** for authenticating with the DataMiner Web Services via SOAP API.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

Configure **credentials** to allow the connector to authenticate via DataMiner Web Services and initiate data retrieval from the Dialog platform.

On the **Polling Config** subpage, you can configure polling settings such as the request size, and you can enable or disable connection requests.

### Dialog Integration Page

This page contains information about this system such as the primary system IP, Dialog version, system role, and integrated element statistics.

The **Protocols** subpage lists the mapped Dialog connectors used to retrieve data on the individual system components.

The **Elements** subpage lists the underlying DataMiner/system elements that contain the polled information. These correspond to the elements displayed in the system web interface.

### Other Pages

The remaining pages contain the specific information for a given system component type.

The additional polled data includes configuration and status information on the platform hub enclosures and hub processing segments, servers, virtual machines, modulators, demodulators, switches, and other components.

The pages visualizes inventory data using a **tree control** to represent the hierarchical structure of Configuration Items (CIs), including:

- **Enclosures (4IF Only)**
- **Virtual Machines**
- **IP Switches**
- **Redundancy Switches**
- **Hub Processing Segments**
- **RF Switching**
- **PTP**
- **Modulators**
- **Demodulators**

Each tree reflects the structure and dependencies of the component types as organized in the source NMS (4IF, XIF, NIF).

Under each CI, the overview of the CI information is also present, which collates information across all elements of that CI Type in a tabular format.

