---
uid: Connector_help_ZTE_ZXDUPA-BCUA
---

## ZTE ZXDUPA-BCUA

The ZTE ZXDUPA-BCUA connector allows you to monitor the device of the same name, focusing on the battery performance, system alarms, and other critical hardware parameters. The ZXDUPA-BCUA is a modular outdoor DC power system used in 3G/4G/5G telecommunication infrastructure, supporting multiple energy sources, including mains, diesel generators, and solar power. This connector helps ensure the effective monitoring of battery health and performance in critical communication systems.

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
   - **Platform Version**: Displays the platform version of the device.  
   - **Software Name**: Shows the name of the software running on the device.  
   - **Software Version**: Displays the current software version.  
   - **MAC Address**: Displays the MAC address of the device.  
   - **IMEI**: Shows the unique International Mobile Equipment Identity of the device.  
   - **Factory Name**: Indicates the manufacturer of the device.  
   - **System Name**: Shows the system name.  
   - **Software Date**: Displays the software build date.

2. **Battery Performance**:  
   - **Battery State of Health Table**: Displays the state of health for all monitored batteries.  
   - **Battery Current Table**: Monitors the current for each battery.  
   - **Battery Voltage Table**: Displays the voltage of each battery.

3. **Battery Alarms**:  
   - **Battery Charge Over Current**: Monitors whether the charge current exceeds safe limits.  
   - **Battery Discharge Over Current**: Monitors whether the discharge current exceeds safe limits.  
   - **Battery State of Change Low**: Indicates when the battery's charge level is critically low.  
   - **Battery Under Voltage**: Monitors when the battery voltage drops below safe limits.  
   - **Battery State of Health**: Displays alarms related to the overall health of the battery.  
   - **Battery High Temperature**: Monitors if the battery temperature exceeds safe operational limits.

4. **System Alarms**:  
   - **Battery Management System Connection Failed**: Indicates when there is a communication failure with the battery management system.  
   - **Inside High Temperature Protect**: Triggers when the internal temperature exceeds safety thresholds.  
   - **Battery Disconnect Unit Communication Failed**: Shows communication issues with the battery disconnect unit.  
   - **Loop Invalid**: Indicates an invalid power loop status.  
   - **Environment High Temperature Protect**: Monitors and triggers when the environmental temperature is too high.  
   - **Environment Low Temperature Protect**: Monitors and triggers when the environmental temperature is too low.

5. **Cell Voltage Alarms**:  
   - **Cell Over Voltage (Li-Ion 1-10)**: Monitors if the voltage of any lithium-ion battery cell exceeds safe limits.  
   - **Cell Under Voltage (Li-Ion 1-10)**: Monitors if the voltage of any lithium-ion battery cell drops below safe limits.
