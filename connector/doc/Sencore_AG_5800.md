---
uid: Connector_help_Sencore_AG_5800
---

# Sencore AG 5800

The Sencore **AG 5800** receiver supports up to 10 decoder cards. It is suited for applications in master control or occasional downlink facilities. It supports all MPEG-4 and MPEG-2 formats up to 10-bit 422 AVC, and up to 16 audio channels in any common format.

## About

This connector uses **SNMP** to retrieve and configure parameters of the Sencore AG 5800. In addition, the connector offers several possibilities for **trending** and **alarm monitoring**.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x | Initial version. | No | Yes |
| 1.0.1.x | - Fixes input primary and secondary source output, making it dynamic and mutually exclusive using labels from transport stream input source. <br>- Fixes output manual format behavior. <br>- Adds overlay image parameters, SCTE35 info, SCTE104 filter mode, and ASI parameters. <br>- Fixes sets for IP address-like and port-like parameters. | No | Yes |
| 1.0.2.x [Main] | Addition of HTTP connection | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 2.5.0                       |
| 1.0.1.x          | 2.5.0                       |
| 1.0.2.x          | 2.5.0                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

#### HTTP Connection (1.0.2.X)

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

HTTP Settings:

- **Username**: The username to request the SID.
- **Password**: The password used in the request to get the SID.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

This page displays information about the device, such as the **System Name**, **System Description**, and **Unit Information**. It also contains page buttons that lead to more information on **In-Band Control**, **Hardware**, **TCP IP**, and the **Sensor.**

### Input

This page displays the input status and configuration. The **Primary** and **Secondary Source** can be set here.

### BISS

This page contains information about BISS and the keys related to it.

### Decoding

This page displays the service information, including the **Service Lock** and **PID Lock**.

### TS

This page displays transport stream information, such as **Input** and **Output Sources**.

### Baseband Processing

This page contains overlay information and ancillary data.

### Audio

This page displays the audio information, including the **Audio Service** and **Discrete** tables.

### Baseband Outputs

This page contains the **SD VANC** and **SD VBI** configuration. It also contains information regarding the **SDI** and **Digital Audio**.

### HD

This page allows you to configure settings related to **VANC/HANC States** and **Lines**.

### Data Outputs

This page displays the **MPEG/IP** information and configuration.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
