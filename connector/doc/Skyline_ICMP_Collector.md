---
uid: Connector_help_Skyline_ICMP_Collector
---

# Skyline ICMP Collector

## About

This connector is part of a generic system that will monitor the connection health of several ICMP-capable devices via ping and aggregate the results to provide an overview of the configured regions and the possible failure.

The connector acts as a collector of the device information loaded by the [Skyline ICMP Platform Manager](xref:Connector_help_Skyline_ICMP_Platform_Manager) backend element.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

This connector works together with the frontend and backend elements of the [Skyline ICMP Platform Manager](xref:Connector_help_Skyline_ICMP_Platform_Manager). As such, you need to make sure those elements are correctly initialized.

After that, on the **Configuration page**, define the **File Import Path** for the file created by the backend element and click the **Import** button.

## How to use

This connector is not meant to be used directly by a user. It is intended to be integrated with the ICMP solution. You only need to make sure the correct initialization procedure, as mentioned above, is applied, so that the connector can function correctly.
