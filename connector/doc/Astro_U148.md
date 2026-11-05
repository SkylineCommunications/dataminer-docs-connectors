---
uid: Connector_help_Astro_U148
---

# Astro U148

## About

This connector can be used with the following devices: **Astro U144**, **U148**, and **U149**. It allows you to gather and view information from these devices as well as configure them.

This connector uses **HTTP** to monitor the device. It also uses an **SNMP** interface to receive traps from the device.

## Key Features

- **Multiplexer matrices**: Configure crosspoints on matrices for CAM MUX and TX MUX.

- **Controller alarm forwarding**: Enable alarm forwarding to the Astro U100 Controller.

- **Service Selection**: Control service assignment to multiplexers.

- **Software Updates**: Upload a firmware archive from the local disk of the DMA.

## Use Cases

### Astro U100 Controller

**Challenge**: To monitor multiple modules at once, communication must be set up through the Astro U100 Controller proxy.

**Solution**: Setting the communication type to `U100C Proxy` will send the requests to the Astro U100 Controller, which will then forward them to the correct Astro module.

**Benefit**: Minimal DataMiner element configuration required to monitor multiple modules.

## Technical Reference

### Prerequisites

- **Minimum DataMiner version**: DataMiner Main Release **10.4.0** or higher is required.

- **Astro API access**: Web interface credentials are required for authentication.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Astro_U148_Technical).