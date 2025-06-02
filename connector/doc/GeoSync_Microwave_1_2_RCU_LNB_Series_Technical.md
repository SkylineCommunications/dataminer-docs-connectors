---
uid: Connector_help_GeoSync_Microwave_1_2_RCU_LNB_Series_Technical
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
- **Device address**: Not required.

SNMP Settings:

- **Port number**: 161 (default)

### Initialization

On initial deployment, some SNMP values may display as **"Not initialized"** until the device completes its boot process and establishes signal synchronization. No additional configuration is required in the DataMiner element after creation.

## How to Use



## Notes

If polling fails, ensure the IP address and network connectivity are correctly configured.
