---
uid: Connector_help_Grass_Valley_UHD1200_Technical
---

# Grass Valley UHD1200

## About

This connector is designed to monitor and control the activity of the **Grass Valley UHD1200** video conversion platform.

The connector uses an SNMP connection to allow the end user to monitor device status and configure video, audio, timing, and metadata processing parameters.

## Configuration

### Connections

#### SNMP Connection — Main

This connector uses an SNMP connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP address or hostname of the device.
- **IP port**: The SNMP port of the device.

SNMP SETTINGS:

- **Get community string**: The community string used for SNMP read operations (default: *public*).
- **Set community string**: The community string used for SNMP write operations (default: *private*).

### Web Interface

The web interface is available when the client machine has network connectivity to the UHD1200 device.

## How to Use

The **Input/Output** page allows selection of video input sources and output destinations. It also provides configuration options for SDI, UHD, and SFP inputs, UHD interfaces, colorimetry, output format, and 2SI mode.

The **Video Processing** page provides controls for video conversion and image enhancement, including processing parameters such as contrast, saturation, and other picture correction settings.

The **Convert Processing** page contains settings for optimizing film-originated content conversion, including cadence detection and film cadence synthesis to improve conversion quality.

The **ARC** page (Aspect Ratio Control) allows configuration of the output aspect ratio and provides manual adjustment of picture size and position.

The **Audio Routing** page enables routing of embedded, AES, or analog audio sources to the available processing channels.

The **Audio AES and Analog** page provides configuration for the device's bidirectional AES and analog audio ports.

The **Audio Shuffle** page allows routing of processed audio pairs to the outputs, including phase inversion and insertion of tone or silence.

The **Audio Control** page provides audio level adjustment and processing controls for each processing channel.

The **Genlock** page contains configuration options for synchronizing the device with external timing references, ensuring proper video and audio synchronization.

The **Timecode** page allows configuration of VITC, LTC, and ATC timecode options for both HD and SD workflows.

The **Metadata** page provides controls for teletext and metadata processing, including configuration of input/output lines and enabling or disabling metadata passthrough.
