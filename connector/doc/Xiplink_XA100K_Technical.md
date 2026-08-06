---
uid: Connector_help_Xiplink_XA100K_Technical
---

# Xiplink XA100K Technical Documentation

## About

The Xiplink XA100K connector provides monitoring of SCPS-based optimization appliances using SNMP. It exposes system health, connection-level protocol metrics, CPU statistics, redundancy parameters, service status, and tunnel information.

## Configuration

### Connections

#### SNMP Connection - XA100K Device

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: Management IP of the XA100K device.
- **Port number**: 161 (default SNMP port).
- **Get/Set community string**: SNMP community string used for polling.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector organizes monitoring information across the following pages: **General**, **Connections**, **CPU Statistics**, **Redundancy**, **Services Status**, **Tunnels**, and **Web Interface**.

### General

The General page provides system-level information:

- System Description
- System Object ID
- System Up Time
- System Contact
- System Health
- System Location
- OS Version
- Device Serial Number
- Link Status Table

### Connections

The connections page contains SCPS and network connection performance metrics:

- Connection Attempts / Accepts / Connects
- Fast Connections Attempts / Accepts
- Non-SCPS Accepts
- SCPS retransmission bits
- SCPS congestion control algorithm
- SCPS proxy uptime
- SNACK / SACK recovery and retransmission metrics
- Largest SNACK hole detection
- SACK recovery cycles and retransmitted segments
- SACK bytes and option block statistics
- Scoreboard overflow indicators

### CPU Statistics

On this page, you can find CPU utilization trend information:

- CPU usage (1 min average)
- CPU usage (5 min average)
- CPU usage (15 min average)
- Maximum CPU values
- Average CPU values

### Redundancy

This page contains redundancy and failover-related parameters for high-availability monitoring.

### Services Status

This page provides service-level monitoring:

- Services count
- Optimized service health
- Quality of service statistics

### Web Interface

This page provides access to the device web interface from DataMiner Cube.
