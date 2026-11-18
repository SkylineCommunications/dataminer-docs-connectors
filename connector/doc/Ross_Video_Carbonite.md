---
uid: Connector_help_Ross_Video_Carbonite
description: "Monitor Ross Video Carbonite switchers in DataMiner, with views of system details, network information, connections, outputs, and input inventories."
---

# Ross Video Carbonite

## About

The Ross Video Carbonite connector presents switcher and video reference information in DataMiner, alongside network details, connections, and input and output inventories.

## Key Features

- **System information**: Review the switcher's operating mode, temperature, video and reference information, and software and hardware versions.
- **Network and connections**: Find Ethernet and IP details alongside dashboard and panel connections.
- **Inputs and outputs**: Browse your device inventory, outputs and on-air outputs, and external and internal inputs.

## Technical Reference

### Configuration

The connector uses one serial connection over IP. When you create the element, enter the switcher's IP address. The default IP port is *5253*. A bus address is not required.

### Monitoring Pages

Use the **General** page for basic device, switcher, video, reference, and temperature information. **Versions** shows software, board, hardware, and FPGA versions, as well as the serial number. **Network** displays Ethernet and IP details, while **Connections** lists dashboard and panel connections.

The **Devices**, **Outputs**, **On Air**, **External Inputs**, and **Internal Inputs** pages show the corresponding device, output, and input information. The **Reference** page provides reference-related information.
