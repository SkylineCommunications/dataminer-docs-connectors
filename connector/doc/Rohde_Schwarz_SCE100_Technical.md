---
uid: Connector_help_Rohde_Schwarz_SCE100_Technical
---

# Rohde Schwarz SCE100 Technical

## About

The Rohde & Schwarz SCE100 is a transmitter exciter used in DAB and DAB+ digital radio networks. It generates precise, high-quality broadcast signals and keeps them synchronized for continuous operation. Operators can also monitor and control it remotely trough this connector, making maintenance faster and more efficient.

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

Underneath the general information, there are three page buttons that lead to the following sub-pages:

- **Software Configuration**: Contains parameters that are used for software configuration of the device.
- **Notifications Configuration**: On this page, the user can configure all the notifications parameters of the device.
- **Device Configuration**: This page contains device configuration parameters, such as the device name, date and time.

### Single Transmitter

This page contains parameter that displays the current status of the transmitter, important transmitter indications and configuration parameters of the transmitter. 

It also contains page buttons to the following sub-pages:

- **Events**: Contains all the possible configurable events of the device.
- **Events Priority**: This page allows the user to configure the priority of the events that are sent by the device.

### Transmitter

This page contains two tables, the top table is contains all the parameters related to the transmitter state.
Underneath the top table, there is a second table that contains all the parameters related to the transmitter commands that the user is able to configure.

It also contains a page button to the following sub-page:

- **Transmitter Notifications**: This page allows the user to configure all the notifications parameters of the transmitter.

### Transmitter Exciter

On this page the user can find two tables, the top table contains all the parameters related to the transmitter exciter state.
Underneath the top table, there is a second table that contains all the parameters related to the transmitter exciter commands that the user is able to configure.

It also contains pages buttons to the following sub-pages:

- **Exciter Notifications**: This page allows the user to configure all the parameters for transmitter exciter notifications.
- **Exciter Automatic**: This page contains a table where the user can configure the automatic parameters of the transmitter exciter.

### Input Interfaces

This page contains four tables, where each table contains parameters related to specific part of the input interfaces of the device.

Following tables are present:

- **Transmitter Input Monitor**: Contains parameters related to the monitoring of the transmitter input.
- **Transmitter Input IP Feed**: Contains parameters related to the IP feed of the transmitter input.
- **Transmitter Input TS Feed**: Contains parameters related to the TS feed of the transmitter input.
- **Transmitter Input General Setup**: This allows the user to configure the source of the transmitter input.

It also contains a page button to the following sub-page:

- **Input Notifications**: This page allows the user to configure all the parameters for input interfaces notifications.

### Input Automatic

This page contains two tables, the top table contains parameters related to the automatic input status.
Underneath the top table, there is a second table that contains all the parameters related to the automatic input commands that the user is able to configure.

It also contains a page button to the following sub-page:

- **Input Automatic Notifications**: This page allows the user to configure all the parameters for automatic input notifications.

### Frequency Regulation

On this page, the user can find two tables, the top table contains parameters related to the frequency regulation state.
Underneath the top table, there is a second table that contains all the parameters related to the frequency regulation commands that the user is able to configure.

It also contains a page button to the following sub-page:

- **Frequency Regulation Notifications**: This page allows the user to configure all the parameters for frequency regulation notifications.

### SFN (Single Frequency Network)

This page contains two tables, the top table contains parameters related to the SFN state.
Underneath the top table, there is a second table that contains all the parameters related to the SFN commands that the user is able to configure.

It also contains a page button to the following sub-page:

- **SFN Notifications**: This page allows the user to configure all the parameters for SFN notifications.

### Precorrection

On this page, the use can find four tables, where the first two table are related to **Liner Precorrection** state and configuration parameters.
Whereas the last two tables are related to **Non-Liner Precorrection** state and configuration parameters.

It also contains page buttons to the following sub-pages:

- **Precorrection Notifications**: This page allows the user to configure all the parameters for precorrection notifications.
- **Signal Quality**: On this page, the user can find parameters related to the signal quality of the precorrection.

### Output Stage

This page contains two tables, the top table contains parameters related to the output stage state.
Underneath the top table, there is a second table that contains all the parameters related to the output stage commands that the user is able to configure.

It also contains a page button to the following sub-page:

- **Output Stage Notifications**: This page allows the user to configure all the parameters for output stage notifications.

### Amplifier

On this page, the user can find three tables, where the first table contains parameters related to the amplifier state.
Underneath the first table, there is a second table that contains all the parameters related to the amplifier commands that the user is able to configure.
The third table contains parameters related to the amplifier PHX 100 parameters.

It also contains a page button to the following sub-page:

- **Amplifier Notifications**: This page allows the user to configure all the parameters for amplifier notifications.

### DVB-T2 Status

This page contains two tables, the top table contains parameters related to the DVB-T2 status.
Underneath the top table, there is a second table that contains all the parameters related to the DVB-T2 TS gateway state.

It also contains a page button to the following sub-page:

- **DVB-T2 Notifications**: This page allows the user to configure all the parameters for DVB-T2 notifications.

### DVB-T2 Setup

On this page, the use can find three tables, where the first table contains parameters related to the DVB-T2 configuration.
Underneath the first table, there is a second table that contains all the parameters related to the DVB-T2 TS localization configuration.
At the bottom of the page, there is a third table that contains all the parameters related to the DVB-T2 TS gateway configuration.

### DVB-T2 Output

This page contains three tables, the top table contains parameters related to the DVB-T2 localization state.
Underneath the top table, there is a second table that contains all the parameters related to the DVB-T2 modulation state.
At the bottom of the page, there is a third table that contains all the parameters related to the DVB-T2 modulation PLP state.

### GNSS (Global Navigation Satellite System)

On this page the user is able to find one table that contains parameters related to the GNSS state.

It also contains page buttons to the following sub-pages:

- **GNSS Notifications**: This page allows the user to configure all the parameters for GNSS notifications.
- **GNSS Configuration**: This page allows the user to configure all the parameters of the GNSS configuration.

### Cooling

This page contains two tables, the top table contains parameters related to the cooling summary state.
Underneath the top table, there is a second table that contains all the parameters related to the cooling state.

It also contains page buttons to the following sub-pages:

- **Cooling Notifications**: This page allows the user to configure all the parameters for cooling notifications.
- **Cooling Configuration**: This page allows the user to configure all the parameters of the cooling configuration.

### Traps

The traps page contains a table with all the relevant information regarding the traps that the device has sent.

It also contains page button to the following subpage:

- **Clean up Configuration**: Contains parameters that will activate automatic cleanup of the traps table.
