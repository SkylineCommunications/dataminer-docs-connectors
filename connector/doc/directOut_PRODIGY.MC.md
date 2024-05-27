---
uid: Connector_help_directOut_PRODIGY.MC
---

# directOut PRODIGY.MC

This connector monitors **PRODIGY.MC** (Modular Audio Converter) through its custom TCP API. PRODIGY.MC is DirectOut's modular audio converter, supporting multiple formats and offering flexible I/O, networked audio, and powerful hardware and software. PRODIGY.MC has been designed to address numerous applications in pro audio, broadcasting, installation, and studio applications, using a single hardware frame.

## About

### Version Info

| Range              | Key Features                                        | Based on | System Impact |
|--------------------|-----------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. Includes all available monitoring. | -        | -             |

### Product Info

| Range     | Supported Firmware                                |
|-----------|---------------------------------------------------|
| 1.0.0.x   | PRODIGY.MC, release version v2.7.2, rev. c24dda7+ |

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

On the **Communication** page, you can see the last sent command and its response.

If you wish to test a command, you can do so by setting the **Outgoing Command Content** parameter to the command you wish to send and then clicking the **Send Command** button. The **Incoming Response Content** parameter will display the response.

The remaining pages display status and settings data:

- General page: Contains system information data.
- Matrix page and subpages: Contains information about inputs/outputs.
- DSP page and subpage: Contains data about the Input Managers and Sum Buses.
- Status page and subpages: Contains all the status-related data.
- Settings page and subpages: Contains all the data related to settings.
- IP Config page: Contains the IP configuration parameters.
- Mirroring page: Contains the mirroring configuration parameters.
- Snapshots page: Contains data about available snapshots.
