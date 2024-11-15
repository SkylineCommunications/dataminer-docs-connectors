---
uid: Connector_help_directOut_PRODIGY.MP
---

# directOut PRODIGY.MP

This connector monitors **PRODIGY.MP** (Modular Audio Processor) through its custom TCP API.

PRODIGY.MP is DirectOut's modular audio processor, designed to address numerous applications in live sound, broadcast, installation, and recording. It provides flexible I/O, dual network audio, DSP functions, sample rate conversion, and powerful hardware and software. Fully modular, the hardware can be configured to specific requirements.

## About

### Version Info

| Range              | Key Features                                        | Based on | System Impact |
|--------------------|-----------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. Includes all available monitoring. | -        | -             |

### Product Info

| Range     | Supported Firmware                                |
|-----------|---------------------------------------------------|
| 1.0.0.x   | PRODIGY.MP, release version v2.7.2, rev. c24dda7  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### TCP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *5003*).

## How to use

This connector uses the DirectOut custom TCP communication protocol. When the element is started, a message is sent to the device to get all current status data. Afterwards, messages will be received from the device whenever a change happens on the device.

To set parameters on the device, a DMA user must have access level 1.

On the **Communication** page, you can see the last sent command and its response.

If you wish to test a command, you can do so by setting the **Outgoing Command Content** parameter to the command you wish to send and then clicking the **Send Command** button. The **Incoming Response Content** parameter will display the response.

The Automatic Request Interval determines how long the system will wait before sending a new GET request if no response is received during that time.

With the timeout status enabled, the system will consider the device as unresponsive if no response is received within the defined timeout period after sending the request.

Please note that it is important to adjust the default timeout settings in the element configuration (under TCP/IP settings) to ensure that the element correctly enters and displays the timeout state if no response is received from the device within the specified period. If the device is found to be unresponsive after the element's timeout period, the system will wait an additional 30 seconds (the default timeout duration in the TCP/IP settings) before marking the element as in a timeout state. To minimize delays, it is recommended to set this value as low as possible.

The remaining pages display status and settings data:

- General page and subpages: Contains system information data.
- Matrix page and subpages: Contains information about inputs/outputs.
- DSP page and subpages: Contains data about the Input Managers, Audio Delays, Sum Buses, Flex Channels, Automix, and Mixers.
- Status page and subpages: Contains all the status-related data.
- Settings page and subpages: Contains all the data related to settings.
- IP Configuration page: Contains the IP configuration parameters.
- Mirroring page: Contains the mirroring configuration parameters.
- Snapshots page: Contains data about available snapshots.
