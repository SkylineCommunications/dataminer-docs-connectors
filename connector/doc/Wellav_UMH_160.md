---
uid: Connector_help_Wellav_UMH_160
---

# Wellav UMH 160

The **Wellav UMH 160** connector is used to monitor and control a **Wellav UMH 160** IRD device.

## About

This connector allows the user to retrieve information about the input and output streams of the device (bit rates, frequency, etc.).

Data is retrieved via the SNMP protocol.

### Version Info

| Range   | Description                                                                                                       | DCF Integration | Cassandra Compliant |
|---------|-------------------------------------------------------------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x | Initial version                                                                                                   | No              | Yes                 |
| 1.1.0.x | Skyline implementation of new range for device with older firmware which was not supported by the previous range. | No              | Yes                 |

### Product Info

| Range   | Device Firmware Version                                                       |
|---------|-------------------------------------------------------------------------------|
| 1.0.0.x | Unknown                                                                       |
| 1.1.0.x | Hardware version: \[V123\]2010.08.04 Software version: \[150.0110\]2012.11.12 |

## Configuration

### Connections - Range 1.0.0.x

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

### Connections - Range 1.1.0.x

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device. The default value is *public*.
- **Set community string**: The community string used when setting values on the device. The default value is *private*.

#### SERIAL Connection

This version of the connector also uses a serial connection to retrieve some data from the HTML pages of the device's web UI (for which SNMP is not available). As such, the following information also has to be specified during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port to retrieve data via HTTP, by default *80*.

- The timeout is set to 2500 ms by default, because the device can be relatively slow when responding to a request.

## Usage (Range 1.0.0.x)

This connector contains 6 pages.

### General Page

This page displays the connection settings of the device (**IP address**, etc.) and the status of the two input slots.

### Input

This page displays parameters related to the three kinds of inputs: Tuner, ASI and IP. For each input, you can click a **Program** button to display the contained programs.

### Output

This page displays data about the current decoding program. You can find the programs list displayed in a table, and select the current program with the **Program Index** selection box.

Information about ASI and IP output are also available here.

### Status

This page contains various parameters with input and output information (lock, bit rates, etc.). These parameters are the most frequently polled by the connector (every 10 seconds by default).

### Alarms

This page displays various alarms. These parameters are not polled from the device, but updated when the associated trap is received.

### Web Interface

The native web interface of the device.

The client machine has to be able to access the device. If not, it will not be possible to open the web interface.

## Usage (Range 1.1.0.x)

### Status

This page displays the main parameters regarding the status of the:

- **Receiver**: Showing the status of the **Signal**, **BER**, **C/N**, the **Input Level**, the **Total** and **Effective TS Rate**.
- **Outputs**: Showing the index of the **Playing Program** and the **PIDs** of **Video**, **Audio1** and **Audio2**.
- **CI**: Showing the status of the **CI Slot 1** and **2**.

### Input

This page displays the configuration of the **Receiver**, i.e. the type of **Source**, **LNB** (**Frequency**, **Voltage** and **22KHz**), **Satellite Frequency**, **Symbol Rate** and **CI MultiDecryption mode. Tuner Type**, **QAM** and **COFDM** information are also displayed.

The page button at the bottom of the page displays the **Program List** table, which contains information regarding all the available received programs.

### Decoder Setup

This page displays the configuration of:

- **Video**, i.e. **Standard**, **Screen Mode**, **Fail Mode**, **DVB Subtitle** and **EBU Subtitle**
- **Audio,** i.e. **Level, Mode** and **Language**
- **SDI/HDMI**, i.e. the **Video Format**

In addition, the name of the **Playing Program** is displayed at the top of the page.

### IP Input

This page displays the configuration of the **Channel**, the **IP Board**, the **Host** and the **FEC parameters.**

### IP Output

This page displays a table with information about the **Channels** in transmission.

### System

This page displays the setup of the **Local** device (i.e. **IP Address**, **Network Mask**, **Gateway**, **MAC Address**, **HW** and **SW Versions** etc.) and the **BISS settings**.

### Web Interface

This page allows you to access the web UI of the device upon login. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
