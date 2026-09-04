---
uid: Connector_help_Techex_Darwin_I-Frame_Switch_Technical
---

# Techex Darwin I-Frame Switch

## About

The **I-Frame Switch** module is a broadcast-grade source switcher that performs frame-accurate switching between I-frame-only video streams such as JPEG XS and I-frame-only H.264/HEVC, typically for redundancy, protection, and contribution workflows.

The **Techex Darwin I-Frame Switch** connector allows DataMiner to monitor and control Techex Darwin I-Frame Switch devices. This connector provides comprehensive monitoring of transport stream processing modules, including configuration management, input/output monitoring, and real-time statistics collection through both HTTP API polling and Kafka message subscriptions.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the Techex Darwin I-Frame Switch device.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: *bypassProxy* (configured by default and disabled for editing).

### Initialization

After creating the element, the following configuration steps are required:

1. Navigate to the **Communication Settings** page.

1. Configure the **Username** and **Password** used to authenticate with the Techex Darwin.

1. Navigate to the **Kafka Settings** page.

1. Configure the Kafka connection parameters for real-time event/statistics streaming.

  Make sure the **Client ID** and **Group ID** are unique in the Darwin system for the messages to properly arrive at the intended DataMiner element.

  The default kafka topics for each module are added automatically when the module data is polled if the correct **Topic Suffix** is configured. You can add other topics using the context menu of the **Kafka Topics** table.

## How to Use

Real-time statistics and performance metrics for modules, inputs, and outputs are updated through the Kafka subscription system for real-time monitoring and displayed on the Statistics page.

To reduce the system load, you can control the polling of each module from the **Modules** table on the **General** page.

Disabling the polling of a module will disable the polling of data through the HTTP connection and disable the Kafka topic subscription. The corresponding data will also be removed from the Module I/O and Statistics tables.
