---
uid: Connector_help_Rohde_Schwarz_SCE100_Technical
---

# Rohde Schwarz SCE100 Technical

## About

The Rohde & Schwarz SCE100 is a transmitter exciter used in DAB and DAB+ digital radio networks. It generates precise, high-quality broadcast signals and keeps them synchronized for continuous operation.

Operators can monitor and control this device remotely through this connector, making maintenance faster and more efficient.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays general device information, such as the device name, model, serial number, and software version.

Underneath the general information, there are three page buttons that lead to the following subpages:

- **Software Configuration**: Contains parameters that are used for software configuration of the device.
- **Notifications Configuration**: Allows you to configure all the notifications parameters of the device.
- **Device Configuration**: Contains device configuration parameters, such as the device name, date, and time.

### Single Transmitter

This page contains parameter that displays the current status of the transmitter, important transmitter indications, and configuration parameters of the transmitter.

It also contains page buttons to the following subpages:

- **Events**: Contains all the possible configurable events of the device.
- **Events Priority**: Allows you to configure the priority of the events that are sent by the device.

### Transmitter

This page contains two tables. The top table contains all the parameters related to the transmitter state. The table below this contains all the parameters related to the transmitter commands you can configure.

It also contains a page button to the following subpage:

- **Transmitter Notifications**: Allows you to configure all the notifications parameters of the transmitter.

### Transmitter Exciter

This page contains two tables. The top table contains all the parameters related to the transmitter exciter state. The table below this contains all the parameters related to the transmitter exciter commands you can configure.

It also contains pages buttons to the following subpages:

- **Exciter Notifications**: Allows you to configure the parameters for transmitter exciter notifications.
- **Exciter Automatic**: Allows you to configure the automatic parameters of the transmitter exciter.

### Input Interfaces

This page contains four tables, each containing parameters related to a specific aspect of the input interfaces of the device:

- **Transmitter Input Monitor**: Contains parameters related to the monitoring of the transmitter input.
- **Transmitter Input IP Feed**: Contains parameters related to the IP feed of the transmitter input.
- **Transmitter Input TS Feed**: Contains parameters related to the TS feed of the transmitter input.
- **Transmitter Input General Setup**: Allows you to configure the source of the transmitter input.

It also contains a page button to the following subpage:

- **Input Notifications**: Allows you to configure the parameters for input interfaces notifications.

### Input Automatic

This page contains two tables. The top table contains parameters related to the automatic input status. The table below this contains all the parameters related to the automatic input commands that you can configure.

It also contains a page button to the following subpage:

- **Input Automatic Notifications**: Allows you to configure the parameters for automatic input notifications.

### Frequency Regulation

This page contains two tables. The top table contains parameters related to the frequency regulation state. The table below this contains all the parameters related to the frequency regulation commands that you can configure.

It also contains a page button to the following subpage:

- **Frequency Regulation Notifications**: Allows you to configure the parameters for frequency regulation notifications.

### SFN (Single Frequency Network)

This page contains two tables. The top table contains parameters related to the SFN state. The table below this contains all the parameters related to the SFN commands that you can configure.

It also contains a page button to the following subpage:

- **SFN Notifications**: Allows you to configure the parameters for SFN notifications.

### Precorrection

This page contains four tables. The first two tables are related to the **Liner Precorrection** state and configuration parameters, and the other tables are related to the **Non-Liner Precorrection** state and configuration parameters.

It also contains page buttons to the following subpages:

- **Precorrection Notifications**: Allows you to configure the parameters for precorrection notifications.
- **Signal Quality**: Displays parameters related to the signal quality of the precorrection.

### Output Stage

This page contains two tables. The top table contains parameters related to the output stage state. The table below this contains all the parameters related to the output stage commands that you can configure.

It also contains a page button to the following subpage:

- **Output Stage Notifications**: Allows you to configure the parameters for output stage notifications.

### Amplifier

This page contains three tables. The first table contains parameters related to the amplifier state. The table below this contains all the parameters related to the amplifier commands that you can configure. The last table contains parameters related to the amplifier PHX 100 parameters.

It also contains a page button to the following subpage:

- **Amplifier Notifications**: Allows you to configure the parameters for amplifier notifications.

### DVB-T2 Status

This page contains two tables. The top table contains parameters related to the DVB-T2 status. The table below this contains all the parameters related to the DVB-T2 TS gateway state.

It also contains a page button to the following subpage:

- **DVB-T2 Notifications**: Allows you to configure the parameters for DVB-T2 notifications.

### DVB-T2 Setup

This page contains three tables. The first table contains parameters related to the DVB-T2 configuration. The table below this contains all the parameters related to the DVB-T2 TS localization configuration. The last table contains all the parameters related to the DVB-T2 TS gateway configuration.

### DVB-T2 Output

This page contains three tables. The top table contains parameters related to the DVB-T2 localization state. The table below this contains all the parameters related to the DVB-T2 modulation state. The last table contains all the parameters related to the DVB-T2 modulation PLP state.

### GNSS (Global Navigation Satellite System)

This page contains a table with parameters related to the GNSS state.

It also contains page buttons to the following subpages:

- **GNSS Notifications**: Allows you to configure the parameters for GNSS notifications.
- **GNSS Configuration**: Allows you to configure the parameters of the GNSS configuration.

### Cooling

This page contains two tables. The top table contains parameters related to the cooling summary state. The table below this contains all the parameters related to the cooling state.

It also contains page buttons to the following subpages:

- **Cooling Notifications**: Allows you to configure the parameters for cooling notifications.
- **Cooling Configuration**: Allows you to configure the parameters of the cooling configuration.

### Traps

The traps page contains a table with all the relevant information regarding the traps that the device has sent.

It also contains page button to the following subpage:

- **Clean up Configuration**: Contains parameters that will activate automatic cleanup of the traps table.
