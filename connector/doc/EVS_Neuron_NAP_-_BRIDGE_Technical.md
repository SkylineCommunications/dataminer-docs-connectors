---
uid: Connector_help_EVS_Neuron_NAP_-_BRIDGE_Technical
---

# EVS Neuron NAP - BRIDGE

## About

TheEVS Neuron NAP - BRIDGE connector enables monitoring and control of Neuron Bridge devices, which provide high-density SDI to IP and IP to SDI conversion. This allows real-time visibility and management of SDI/IP bridging operations within broadcast environments.

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (fixed value: *2072*).

## How to use

### General Page

The **General** page provides essential device identity information, such as the card name, product version, and user labels. It also displays overall polling progress and offers quick access to the **Debug** page for troubleshooting.

### General Settings Page

On the **General Settings** page, you can configure key operational parameters, including **input selection** (auto, main, or backup), **lock mode and status**, and **switch-back functionality**. This page also allows you to manage **PTP** settings and **make-before-break switching** options, which are important for device synchronization and seamless switching.

### Network Settings Page

The **Network Settings** page is where you monitor and configure network interfaces. Here you can enable or disable **bandwidth monitoring** and view or edit **MAC settings**, including **IP configuration, addresses, netmask, gateway**, and **FEC (Forward Error Correction)** for each network interface.

### Video Paths Page

For video routing and monitoring, the **Video Paths** page displays available video formats and allows you to configure **main and backup input sources, color space**, and **switching status** for each video path.

### IP Video I/O and IP Audio I/O Pages

The **IP Video I/O** and **IP Audio I/O** pages provide detailed tables for monitoring and configuring IP-based video and audio streams, including their **status, format**, and **labels**.

### SDI I/O Page

The **SDI I/O** page is dedicated to SDI channel monitoring and control. You can view the **status** of each SDI input and output, check **video formats**, and manage **OSD (On-Screen Display) settings** and **path selection**.

### Debug Page

For troubleshooting and advanced operations, the **Debug** page offers controls to **refresh data, cancel polling, clear tables, enable or disable debug logging**, and view **error messages**. This page is useful for resolving communication issues or verifying device responses.

## DataMiner Connectivity Framework

The **1.0.0.x** range of the EVS Neuron NAP - BRIDGE connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).
