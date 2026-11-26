---
uid: Connector_help_ELTI_TERX_Series_Technical
description: "Learn how to use the ELTI TERX Series connector, including the SNMP connections to the changeover controller and the exciters, and the changeover, power supply, safety input, and RF pages."
---

# ELTI TERX Series

## About

ELTI TERX transmitters are digital TV transmitters and exciters that are typically deployed in a changeover (redundancy) setup, in which two transmitting devices and a reserved device are supervised by the changeover controller (ECOS) of the system.

This connector retrieves information from the TERX system via SNMP and, through two additional SNMP connections, from the two TERX exciters. It monitors the agent information, the changeover status and configuration, the cooling data, the power supplies, the safety inputs, the summary warnings and alarms, and the RF power and frequency of each exciter, and allows the changeover to be configured from DataMiner.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection to the TERX system (changeover controller) and requires the following input during element creation:

- **IP address/host**: The polling IP of the TERX system.
- **IP port**: The IP port of the TERX system, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### SNMP Connection - Transmitter 1 and SNMP Connection - Transmitter 2

These two SNMP connections point to the standalone TERX exciters and are used only for the **Forward Power**, **Reflected Power**, and **TX Frequency** parameters of exciter 1 and exciter 2 on the RF Power and Frequency page. They require the following input during element creation:

- **IP address/host**: The polling IP of the exciter.
- **IP port**: The IP port of the exciter, by default *161*.
- **Get community string**: The community string used when reading values from the exciter (default: *public*).
- **Set community string**: The community string used when setting values on the exciter (default: *private*).

Both exciter connections are polled every minute. When an exciter does not respond, its **Forward Power**, **Reflected Power**, and **TX Frequency** parameters are not updated and the corresponding **VSWR** shows *N/A*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

All status pages are polled once a minute. The **Contact Info** table on the General page is polled once an hour.

### General Page

This page shows the device type (*Transmitter* or *Repeater*), the device configuration (*Standalone* or *Exciter*), the serial number, the agent version, the location, and the agent uptime of the device.

The **Web Interface** parameter holds the address used by the Web Interface page. It is filled in automatically with the polling IP of the main connection the first time the element starts, and can be changed afterwards if the web interface is reachable on a different address.

The **Contact Info** table lists the contacts configured on the device. The name, email, and phone of each contact can be edited from DataMiner.

### Changeover Status Page

This page shows the **Device Mode** of the changeover system (*Auto*, *Manual*, *Off*, *Standby*, *Standby Complete*, or *Standby Because of RF Switch*) and, for **Device 1** and **Device 2**, the RF information (*Dummy Load* or *Antenna*), the RF connection, the device state (*Off* or *On*), the device mode (*Manual* or *Auto*), whether the device is connected, the output power, and the communication status (*Communication Ok* or *Communication Error*).

The **Reserved Device** section shows the same information for the reserved device, and **Reserved Device Select** indicates whether the reserved device is in standby (*Standby Device*) or is currently working as *Device 1* or *Device 2*.

### Changeover Info Page

This page shows the current status of the changeover: general and changeover standby, Auto/Manual and Local/Remote mode, general and changeover reset, user authorization, and the **RF Switchover Mode**, which indicates whether the switchover is in *Auto* or *Manual* mode and which device (A or B) is connected to the antenna.

### Changeover Configuration Page

This page contains the settings that can be written to the TERX system:

- **Auto/Manual Configuration** and **Remote/Local Configuration**: Select the operating mode of the changeover.
- **General Standby** and **Changeover Standby**: Send a standby command to the whole system or to the changeover only.
- **General Reset** and **Changeover Reset**: Send a reset command to the whole system or to the changeover only.
- **RF Switch Change Position 1** and **RF Switch Change Position 2**: Change the position of the RF switches. The value returns to *Not Active* automatically once the change has taken effect.
- **Transmitting Device 1 Configuration**, **Transmitting Device 2 Configuration**, and **Reserved Device Configuration**: Switch the corresponding device *On* or *Off*.

The current values of these settings as reported by the device are shown next to them on the same page.

### Changeover LC Data Page

This page shows the liquid-cooling data of the system: the maximum power amplifier temperature, the water temperature, the pressure, the **Water Pump Status** (pump A and/or B OK or failing), and **Water Pump Active** (which pumps are working).

### Power Supply Page

This page shows whether the 5 V, 12 V, and 24 V supplies are within range, with a separate *Voltage Low* and *Voltage High* indication for each supply.

### Safety Input Page

This page shows the safety inputs of the system: external standby, system power supply, dummy load, general standby, AC power fault, UPS fault, and two additional input status indications.

### General Failure Page

This page shows the summary warning and summary alarm of the system and of the changeover, which indicate whether there are any active warnings or alarms on the device.

### RF Power and Frequency Page

This page shows, for each exciter, the **TX Output Power** as a percentage reported by ECOS, and the **Forward Power** and **Reflected Power** in watts and the **TX Frequency** in hertz polled directly from the exciter over its own SNMP connection. The **VSWR** of each exciter is calculated by the connector from the forward and reflected power, and shows *N/A* when the calculation is not possible (for example when the forward power is zero or the reflected power is not lower than the forward power). By default, a VSWR above *1.5* raises a warning and a VSWR above *2.0* a critical alarm. All values on this page are trended.

### Web Interface Page

This page embeds the web interface of the device, using the address in the **Web Interface** parameter on the General page.
