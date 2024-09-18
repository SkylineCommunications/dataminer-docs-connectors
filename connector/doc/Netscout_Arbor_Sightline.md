---
uid: Connector_help_Netscout_Arbor_Sightline
---

# Netscout Arbor Sightline

## Netscout Arbor Sightline

The Netscout Arbor Sightline connector allows you to monitor the device, focusing on its general system parameters, CPU, memory usage, total flows, and interface statistics. Netscout Arbor Sightline is a powerful platform for network-wide infrastructure security, offering both macro and micro-level visibility into traffic. This enables you to identify threats and optimize network performance.

---

### About

#### Version Info

| Range       | Key Features    | Based on | System Impact |
|-------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

---

### Product Info

| Range      | Supported Firmware |
|------------|--------------------|
| 1.0.0.x    | N/A                |

---

### System Info

| Range      | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x    | No              | Yes                 | -                 | -                   |

---

### Configuration

#### Connections

**SNMP Connection - Main**  
This connector uses a Simple Network Management Protocol (SNMP) connection. It is the main connection used to retrieve all the data. During element creation, it requires the following input:

**SNMP CONNECTION:**

- **IP address/host:** The polling IP or URL of the destination.  
- **IP port:** The IP port of the destination.

**SNMP Settings:**

- **Get community string:** The community string used when reading values from the device (default: public).  
- **Set community string:** The community string used when setting values on the device (default: private).

---

### How to use

This connector is primarily used for monitoring purposes. Across the connector, several parameters can be configured according to your preferences. It is recommended to use the connector with alarm and trend templates to enable alarm monitoring and trending of parameters.

---

### Device Information Monitored

1. **General System Parameters**:  
   - **Description**: Displays general system details, including the device's name, uptime, contact, and location.
   - **Object ID**: Shows the unique identifier for the device.
   - **System Uptime**: Displays how long the system has been running.
   - **Device Name**: Shows the name of the device.
   - **Location**: Displays the location of the device (if configured).

2. **CPU**:  
   - **Average Device CPU Load**: Displays the average CPU load of the device over three different time intervals: 1 minute, 5 minutes, and 15 minutes.

3. **Memory**:  
   - **Device Physical Memory**: Monitors the memory usage, including memory available, memory in use, and overall memory usage.
   - **Device Swap Space**: Displays the available and used swap space, including percentage usage.
   - **Disk Usage**: Shows the usage of the device's disk space.

4. **Flows**:  
   - **Device Total Flows**: Displays the total number of flows being monitored by the device.
   - **Device Total Flows HC**: Displays high-capacity total flows, providing additional flow information.

5. **Interface Information**:  
   - **Detailed Interface Table**: Lists detailed interface data, including the display key, interface name, operational and administrative statuses, physical addresses, packet rates, and bitrates.
