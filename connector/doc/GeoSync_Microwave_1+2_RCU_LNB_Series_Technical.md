---
uid: Connector_help_GeoSync_Microwave_1+2_RCU_LNB_Series_Technical
---

# Connector Technical Documentation – GeoSync Microwave 1+2 RCU LNB

## About

The GeoSync Microwave 1+2 RCU LNB Series connector enables seamless integration of 1+2 Low-Noise Block downconverter (LNB) redundancy systems with DataMiner, ensuring optimal performance and reliability in satellite communication infrastructures. Designed to support both manual and automatic switching, the connector facilitates real-time monitoring and control via SNMP, offering robust visibility into device status, signal paths, and power configurations.

It provides operators with access to a wide range of operational parameters, such as signal strength and lock status, along with switch positions and redundancy configurations, including priority settings and failover status. This integration empowers broadcasters and satellite operators to proactively manage their infrastructure, reduce downtime, and streamline operations from a centralized, user-friendly interface.

## Configuration

### Connections

#### SNMP Connection

This connector uses a **Simple Network Management Protocol (SNMP)** connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP address of the GeoSync Microwave LNB device.

SNMP Settings:

- **Port number**: 161 (default)

### Initialization

On initial deployment, some SNMP values may display as **"Not initialized"** until the device completes its boot process and establishes signal synchronization. No additional configuration is required in the DataMiner element after creation.

## How to Use

The GeoSync Microwave 1+2 RCU LNB connector provides an intuitive interface organized into four dedicated pages, each designed to streamline monitoring and control operations.

### General Page
This page offers an overview of the system and its components. It includes read-only parameters that display key information such as:

- **System Description** – General identification of the system.
- **LNB Model** – Type/model of each connected LNB.
- **LNB Serial Number** – Unique hardware identifiers.
- **Firmware Revision** – The current firmware version running on the system.

This information helps operators quickly verify the hardware setup and identify the system during troubleshooting or maintenance.

### Switch Control Page
This page allows users to configure the redundancy behavior and manage LNB switching operations:

- **LNB Operating Mode** – Select between **Manual** and **Automatic** switching modes.
- **LNB Switch Position** – Use the dropdown menu to determine which LNB is currently in standby mode.
- **LNB Priority** – Set priority for each LNB, indicating which unit should take over in case of failover.

These controls offer flexibility in managing signal paths and handling redundancy preferences in real-time.

### LNB Power Page
On this page, users can manage power distribution to each LNB with detailed settings:

- **LNB Naming** – Assign custom labels to LNB 1, LNB 2, and the Backup LNB for easier identification.
- **Voltage Assignment** – Set voltages for both low and high bands of each LNB individually.
- **Power Limits** – Define high and low voltage thresholds for each LNB to ensure safe and stable operation.

These settings allow for precise control over power management, helping protect hardware and maintain signal integrity.

### Status/Alarm Page
This page provides real-time feedback on system health and alarm conditions:

- **Alarm Statuses** – Monitor the status of critical components including:
  - PS A 6V & 28V  
  - PS B 6V & 28V  
  - LNB 1, LNB 2, LNB 3 (Backup)  
  - Transfer Switch 1 & 2 Contacts  
  - Internal Communication  
- **Power Supply Voltages** – View the current voltage levels delivered by the power supplies.
