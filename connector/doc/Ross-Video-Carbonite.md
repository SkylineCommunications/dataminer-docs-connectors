---
uid: Connector_help_Ross-Video-Carbonite
description: >-
  Monitor Ross Video Carbonite switchers in DataMiner, with views of system details, network information, connections, outputs, and input inventories.
---

# Ross-Video-Carbonite

## About

The Ross Video Carbonite connector presents switcher and video-reference information in DataMiner, alongside network details, connections, and input and output inventories.

## Key Features

- **System information**: View switcher mode, device details, temperature, video and reference information, and software, board, hardware, and FPGA versions.
- **Network and connections**: Review Ethernet and IP details, dashboard connections, and panel connections.
- **Inputs and outputs**: Browse device inventory, outputs and on-air outputs, and external and internal inputs.

## Configuration

The connector uses one serial connection over IP. When you create the element, enter the switcher's IP address. The default IP port is *5253*. A bus address is not required.

## Monitoring Pages

Use **General** for basic device, switcher, video, reference, and temperature information. **Versions** shows software, board, hardware, and FPGA versions, as well as the serial number. **Network** displays Ethernet and IP details, while **Connections** lists dashboard and panel connections.

The **Devices**, **Outputs**, **On Air**, **External Inputs**, and **Internal Inputs** pages show the corresponding device, output, and input information. The **Reference** page provides reference-related information.
