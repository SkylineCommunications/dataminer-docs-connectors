---
uid: Connector_help_Evertz_ev670-X45-HW_U8E8D
---

# Evertz ev670-X45-HW U8E8D

TThis connector can be used to monitor and configure the Evertz ev670-X45-HW U8E8D. This is an FPGA-accelerated compute blade that supports both 12G/3G/HD-SDI and IP interfaces.

## About

### Version Info

| Range   | Key Features            | Based on | System Impact |
|---------|-------------------------|----------|---------------|
| 1.0.0.x | Initial implementation. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The IP port of the destination (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector polls most of the tables using subtable functionalities to reduce the amount of time it takes to poll tables and also to poll essential rows.

In range **1.0.0.x**, the following pages are available in the element:

- **General**: Includes parameters that match the "System" page on the device such as the Build Time and CPU Temperature. This also includes a parameter named **Amount of Outputs to show**, which can be toggled to **show all the outputs** that the device provides in all of the tables or to just show the **first 8 outputs in all of the tables**.
- **Network Management**: Includes all of the network management tables such as Control Port Configuration, Data Port Configuration, RS-FEC Control, Data Port Monitor, Magnum In-Band Controller, Time Management, NTP Server, and SNMP Trap Servers.
- **Product Features**: Includes the support statuses of each of the product features and their licenses.
- **Timing**: Includes various PTP and Genlock-related configuration parameters.
- **NMOS Control**: Includes parameters for adjusting the NMOS control such as the Unicast Domain and Nameserver.

- **SDI Input**: Includes the SDI Input table.
- **Compressed IP Input**: Includes the Compressed Stream MPPM Control and Compressed IP Input tables.

- **Video** **Control**: Includes the Video SDI Output table.
- **Audio** **Control**: Includes the Audio Shuffling, Audio Shuffling Control, and the SDI Output tables.
- **ANC** **Control**: Includes the VPID Control table.
- **Compressed IP Output**: Includes the Compressed IP Output Configuration table.
- **Video (S2110-20,22) IP Output**: Includes the RTP Payload Type parameter and the Video IP Output Configuration Control table.
- **Audio (S2110-30) IP Output**: Includes the Audio RTP Payload Type and AES67 IP Output Packet Time parameters as well as the Audio IP Output Channel Configuration and Audio IP Output tables.
- **ANC (S2110-40) IP Output**: Includes the ANC RTP Payload Type parameter as well as the ANC IP Output table.

- **Encoder** **Control**: Includes the Encoder Control and Encoder Audio Output Control tables.
- **Decoder** **Control**: Includes the Decoder Input Monitor and Decoder Input Control tables.

- **Compressed Video IP Input Monitor**: Includes the Compressed Video IP Packet Monitor, Compressed Video IP Packet Clear, and Input Stream Internal Decoder Core tables.
- **Internal Decoder Core**: Includes the Internal Decoder Core table.

- **System** **Notify**: Includes the System Faults table.
- **Input** **Notify**: Includes the SDI Input Monitoring and Faults table. The Monitoring table can be used for alarm monitoring while the Faults table can be used to enable or disable traps.
- **Decoder** **Notify**: Includes the Decoder Monitoring and Faults table as well as the Decoder MPPM Monitoring and Faults table. The Monitoring table can be used for alarm monitoring while the Faults table can be used to enable or disable traps.
- **Traps**: Includes the Traps Log table and trap control parameters.
