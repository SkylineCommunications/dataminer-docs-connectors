---
uid: Connector_help_SISELECTRON_SR1_Technical
---

# Siselectron SR1

This is a DataMiner connector for the **Siselectron SR1**, a rack mount server that utilizes Synamedia's Media Edge Gateway, which can be used for decoding, encoding, and transcoding/processing.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **Authentication** page of the element, fill in the username and password to connect to the device.

## How to Use

This connector has the following main sections:

- **Channels**: This is identical to the main page of the device, where you can monitor and edit the settings applied on each of the channels active on the device.
- **Input Settings**: Includes the **DVBS2 Settings** and **SDI Settings** pages, which allow you to monitor and edit the input TS and input service settings for either standard.
- **Descrambling**: Allows you to see all the available descramblers and adjust the descrambling mode.
- **Output Settings**: Includes the **Output TS**, **Output Service**, and **SDI Outputs** pages, which allow you to monitor and edit the output TS and output service settings.
- **Encoders and Decoders**: Includes the tables for each of the encoders and decoders, which covers features like **Video Pre-Processing**, **Basic Video Settings**, **Basic Audio Settings**, and more features of the device.
- **Configuration**: Allows you to view and monitor the data for the current **Licenses**, **Last 500 Historic Alarms**, and **PCIe Cards**.
