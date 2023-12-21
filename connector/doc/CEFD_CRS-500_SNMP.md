---
uid: Connector_help_CEFD_CRS-500_SNMP
---

# CEFD CRS-500 SNMP

The CRS-500 is Comtech EF Data's next generation 1:N Redundancy System. It is compatible for use with the CEFD CDM-625 and CEFD CDM 750 Modem.

## About

The CEFD CRS-500 SNMP connector is designed to monitor and control a CEFD CRS -500 device via SNMP. The different parameters of this device are available on different pages. The layout is based on the web interface of the device.

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version | - | - |
| 1.0.1.x [SLC Main] | Multiple tables now use naming instead of displayColumn to make these tables Cassandra-compliant. | 1.0.0.1 | - |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | No                      | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

**SNMP CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.
- **Device address**: N/A

**SNMP Settings**:

- **Port number**: the port of the connected device, default *161*.
- **Get community string**: the community string in order to read from the device. The default value is *public*.
- **Set community string**: the community string in order to set to the device. The default value is *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### Config - Redundancy page

On this page, you can find multiple groups of parameters. The value of these parameters can be set to the preferred value.

### Config - Modem page

On the **Config- Modem** page, two tables are available:

- **Traffic Modem Configuration Table**: Allows you to view and configure information on the different modems.
- **Redundant Modem Configuration Table**: Allows you to view and configure information on the redundant modem.

### Config - Remote Management page

On this page, you can view and configure the **Network Settings** and the **SNMP Configuration**.

### Status - Monitor page

On the **Status - Monitor** page, you can view status information for the **Redundancy System**. Underneath that, the **Slot Status Table** is displayed.

### Status - Event Log page

Here the **Event Log Table** can be viewed.

You can clear this table by pressing the **Clear** button.

### Utility - Info page

On the **Utility - Info** page, you can view the **General Configuration**, **Time and Data**, and **Bulk Information**. Some of these parameters can also be modified.

### Utility - Boot Slot

On this page, you can select a firmware image to boot from. You can also reboot the device by clicking the **Reboot** button.

### Webpage

Here the web interface of the device can be viewed.
