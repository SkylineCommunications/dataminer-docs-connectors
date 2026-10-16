---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Transportstream_Discovery_Technical
description: Configure and use the Transportstream Discovery connector in DataMiner, with connection settings and operational guidance.
---

# Vodafone Kabel Deutschland GmbH Transportstream Discovery

## About

The Vodafone Kabel Deutschland GmbH Transportstream Discovery connector discovers transport streams, services, and PIDs from elements using supported connector types, including CISCO DCM.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

On initialization of the connector, the number of elements for the supported discovery protocols will be displayed in the **Discovered Protocols** table.

In the **Discovered Elements** table, all individual elements found in the DMS will be listed. By default, data polling will be *disabled*.

To enable polling of an element, click the **Include** button.

On the **Settings** page, you can configure the polling frequency of all enabled elements. By default, the **Discover Frequency** is set to *6 hours*.

All polled information for every individual element will be aggregated in an overview table.

Data related to transport streams, services, and PIDs can be found on the **TS Database**, **Service Database**, and **PID Database** pages, respectively.
