---
uid: Connector_help_Newtec_Dialog_Infrastructure
---

# Newtec Dialog Infrastructure

The Newtec Dialog Time Infrastructure connector collects and organizes data related to the hardware and operating system infrastructure that supports the Newtec Dialog VSAT Platform.

The Newtec Dialog monitoring system collects metrics from the Newtec dialog platform and stores them in a Time Series database. The connector retrieves data from the Newtec Dialog Platform via its **REST API** and via the **TSDB API**. Data from both sources is aggregated into the connector.

The connector uses the Dialog SOAP to poll the data from the central Dialog NMS. The collected data includes system configuration and status information on the platform hub enclosures and processing segments, servers, virtual machines, modulators, demodulators, switches, and other components.

## About

### Version Info

| Range              | Key Features                              | Based on | System Impact |
|--------------------|-------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version                           | -        | -             |

### Product Info

| Range              | Supported Firmware       |
|--------------------|--------------------------|
| 1.0.0.x            | 2.2.1, 2.2.2, 2.4.2      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection - 1

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The IP of the Newtec Central NMS.
- **IP port**: *80*
- **Device address**: *BypassProxy*

## How to Use

### General Page

On this page, you can configure and apply the **credentials** for user authentication of the SOAP API in order to collect data from the Dialog platform.

On the **Polling Config** subpage, you can configure polling settings such as the request size, and you can enable or disable connection requests.

### Dialog Integration Page

This page contains information about this system such as the primary system IP, Dialog version, system role, and integrated element statistics.

The **Protocols** subpage lists the mapped Dialog connectors used to retrieve data on the individual system components.

The **Elements** subpage lists the underlying DataMiner/system elements that contain the polled information. These correspond to the elements displayed in the system web interface.

### Other Pages

The remaining pages contain the specific information for a given system component type.

The additional polled data includes configuration and status information on the platform hub enclosures and processing segments, servers, virtual machines, modulators, demodulators, switches, and other components.
