---
uid: Connector_help_Snell_Wilcox_IQOSY30
---

# Snell Wilcox IQOSY30

## About

The Snell Wilcox IQOSY30 is a 3G/HD/SD-SDI frame synchronizer with fiber interfacing.

In the 1.0.0.x range of this connector, DVEs are generated for each module in the Module table.

While the 1.0.0.x branch of the connector uses SNMP communication, the 2.0.0.x branch, which is the main branch, uses the RollCall communication protocol.

## Configuration

### Connections

### SNMP Connection (1.0.0.x range)

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

**SNMP Settings**:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

### Serial Connection - RollCall (2.0.0.x range)

- **IP address/host**: The polling IP of the device.
- **IP port**: The port of the connected device.
- **Bus address**: The bus address of the connected device, specified in XX.XX format.

## Usage

### General

This page contains general device parameters, such as **Serial Number** and **Software Version**, and a page button, **Fiber**.

### Video

This page contains video control parameters and a **Pattern and Caption** page button.

### Procamp

This page contains Procamp parameters.

### Genlock

This page contains Genlock parameters.

### Embedders

This page contains Embedder status parameters and page buttons for the Embedder control parameters.

### Audio

This page contains Audio status and control parameters and a **Dolby E** page button.

### Logging

This page contains page buttons for **Logging Misc**, **Logging Video Input**, **Logging Reference**, **Logging Audio Input**, **Logging Video Output**, **Logging Fiber** and **Logging Audio Output**.

### Rolltrack

This page contains Roll Track parameters and a button to **Restart** the device.

### Embedder Router (2.0.0.x range)

This page features a matrix that visualizes the routing of embedders and enables you to control the routing directly.
