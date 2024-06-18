---
uid: Connector_help_ETL_Systems_ALTO_C304
---

# ETL SYSTEMS ALTO C304

This ALTO amplifier chassis is a configurable, redundant amplifier fitted with six hot-swap amplifier modules, which will typically provide four channels of redundant amplification.

The unit is usually arranged as four main amplifier modules and two standby modules.

## About

### Version Info

| Range   | Key Features                                                   | Based on | System Impact |
|---------|----------------------------------------------------------------|----------|---------------|
| 1.0.0.x | - Initial version. <br>- Compatible with Skyline EPM Solution. | -        | -             |
| 1.0.1.x | - Removed display key column from the Set Path Module Table. <br>- Added the Module Used column to the Set Path Module Table.| -        | -             |

### Product Info

| Range    | Supported Firmware |
|----------|--------------------|
| 1.0.0.x | ALTO Amplifier     |
| 1.0.1.x | ALTO Amplifier     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The IP address of the device, e.g. *10.11.12.13*.
- **Device address**: Not required.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

### General

The **General** page displays an informative overview of the system's current status.

The **Module Readings Table** displays critical parameters such as Optical Power (OP), Laser Diode Bias Current (LNB Current), and voltages across multiple amplifiers, which are indicative of each module's operational health.

The **Chassis Readings** Table gives a summary of system-wide power statistics, including Power Supply Unit (PSU) voltages and fan speeds, to provide a comprehensive snapshot of the system's power infrastructure.

### Module Settings

On the **Module Settings** page, you can find the tools necessary for adjusting individual module characteristics.

The **Module Settings Table** allows you to configure gains, slopes, power levels, and Low Noise Block (LNB) states, among other settings. This way, you can tailor each module's performance parameters to meet specific operational requirements.

### Systems Settings

The **System Settings** page is designed for the modification and management of overarching system parameters. It allows you to set the main and redundant module numbers, which are integral to the system's failover strategy. The Tracking parameter allows you to control the system's tracking behavior.

The page also includes the **Set Path Module Table**, **Hot Standby Redundancy Table**, and **Cold Standby Redundancy Table**. These tables offer read and write access, allowing you to modify module paths and configure the redundancy setup of the system, whether it be for immediate failover through hot standby or for manual intervention through cold standby.
