# Norsat 1:1 LNB Redundant Controller
### Intelligent LNB Redundancy, Monitoring and Protection

---

## Overview

The **Norsat 1:1 LNB Redundant Controller** provides centralized monitoring, configuration, and protection for redundant LNB systems, enabling operators to maintain reliable signal reception and quickly respond to abnormal LNB operating conditions.

The DataMiner connector provides a clear operational view of the redundant LNB system, including active and standby device status, LNB measurements, operating configuration, and alarm conditions.

---

## Functionality

### LNB Control and Redundancy

Monitor and manage the active and standby LNB devices from a single DataMiner element.

Operators can view the currently active device, identify the standby device, and select a different active device when required. Automatic mode override provides additional control over the redundancy operating mode.

---

### Real-Time LNB Measurements

Gain immediate visibility into the operating conditions of the connected LNBs.

The connector provides measurement information including:

- LNB frequency band
- LNB 1 current
- LNB 2 current
- LNB 3 current

Current measurements are displayed in milliamps, allowing operators to quickly identify abnormal power consumption or LNB operating conditions.

---

### Flexible Device Configuration

Configure supported redundant controller settings directly from the DataMiner interface.

The connector provides user-editable configuration for:

- **ULC Status**
- **Number of Supported Multiband LNB Bands**

Configuration changes are sent directly to the controller using SNMP SET operations, providing centralized control without requiring access to the device's local interface.

---

### Configurable LNB Protection

Define current warning and fault thresholds to provide protection against abnormal LNB current conditions.

Operators can configure:

- **Maximum Current Fault Threshold**
- **Minimum Current Fault Threshold**
- **Maximum Current Warning Threshold**
- **Minimum Current Warning Threshold**

The configurable thresholds allow the monitoring system to distinguish between warning-level conditions and more serious fault conditions.

---

### Clear Alarm Visibility

The dedicated **Alarms** page provides a centralized view of active LNB faults and warnings.

Operators can quickly identify abnormal operating conditions and determine when intervention may be required, helping reduce troubleshooting time and improve system availability.

---

### Centralized Operational Control

The connector brings monitoring and configuration of the Norsat redundant controller into the DataMiner environment.

This provides operators with a single operational interface for:

- Monitoring LNB status
- Reviewing LNB measurements
- Managing redundancy settings
- Configuring operating parameters
- Defining protection thresholds
- Monitoring active alarms

---

## Use Cases

- **Satellite Ground Stations**  
  Monitor and manage redundant LNB systems supporting satellite reception infrastructure.

- **Broadcast and Media Networks**  
  Maintain reliable LNB operation for critical satellite signal reception and distribution.

- **Teleport Operations**  
  Provide centralized visibility and control of LNB redundancy across operational infrastructure.

- **Proactive LNB Monitoring**  
  Detect abnormal current conditions before they develop into more serious equipment failures.

- **Operational Troubleshooting**  
  Quickly identify active, standby, warning, and fault conditions from a centralized monitoring platform.

---

## Business Impact

- Improve LNB system availability through effective redundancy management
- Reduce troubleshooting time with centralized status and measurement visibility
- Detect abnormal LNB current conditions through configurable thresholds
- Reduce manual intervention through centralized configuration
- Improve operational awareness with clear alarm and warning information
- Simplify management of redundant LNB infrastructure through DataMiner

---

## Why It Matters

Reliable satellite reception depends on maintaining the health and availability of critical LNB infrastructure.

The **Norsat 1:1 LNB Redundant Controller** connector brings redundancy management, real-time measurements, configurable protection thresholds, and alarm visibility together within DataMiner.

By combining operational monitoring with centralized configuration and protection, it gives operators the information and control needed to maintain reliable LNB operation and respond quickly when conditions change.

---