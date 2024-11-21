---
uid: Connector_help_ZTE_ZXONE_9700
---

# ZTE ZXONE 9700

The ZTE ZXONE is a versatile optical transport network device that supports efficient and scalable communication infrastructure for telecom networks. The ZTE ZXONE connector enables monitoring of this device, focusing on system performance, interfaces, optical transport network (OTN) metrics, and alarms. This connector ensures comprehensive monitoring of key parameters for optimal network operation.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.1 [Initial] | SNMP-based monitoring of system, interfaces, OTN, and alarms | - | Low |

### Product Info

| Range      | Supported Firmware |
|------------|--------------------|
| 1.0.0.1    | ZTE ZXONE 9700 V1.10.010.001 |

### System Info

| Range      | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.1    | No              | No                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection as the primary method for data retrieval. During element creation, the following inputs are required:

**SNMP CONNECTION:**

- **IP address/host:** The IP or URL of the destination device (10.3.21.114).
- **IP port:** The IP port of the destination device.

**SNMP Settings:**

- **Get community string:** The community string for reading values from the device (default: *public*).
- **Set community string:** The community string for setting values on the device (default: *private*).

## How to Use

The ZTE ZXONE connector is used for detailed device monitoring. Parameters can be configured to meet operational requirements, and the connector is best used with alarm and trend templates for effective monitoring and performance analysis.

### Device Information Monitored

#### General System Parameters

- **Platform Version**: Displays the platform version of the device.
- **Software Version**: Shows the software version installed on the device.
- **Uptime**: Indicates the total uptime of the device.
- **Service Layers**: Displays the availability of each OSI layer (e.g. Physical Layer, Data Link Layer).

#### Interface Parameters

- **Type**: Displays the interface type.
- **MTU**: Shows the Maximum Transmission Unit size for each interface.
- **Speed**: Displays the interface speed.
- **Status**: Indicates the administrative and operational status.
- **Bit Rate**: Shows the inbound and outbound bitrate for each interface.

#### Optical Transport Network (OTN) Metrics

- **Input Optical Power**: Displays the input power level.
- **Output Optical Power**: Displays the output power level.
- **Module Temperature**: Shows the temperature of OTN modules.
- **Bit Error Rate (BER)**: Monitors BER before Forward Error Correction (FEC).

#### Alarms

- **Code**: Unique identifier for the alarm.
- **Level**: Indicates the severity of the alarm (e.g. Alert, Warning).
- **Description**: Provides details about the alarm, including port, channel, and type.
- **Timestamp**: Logs when the alarm occurred.
