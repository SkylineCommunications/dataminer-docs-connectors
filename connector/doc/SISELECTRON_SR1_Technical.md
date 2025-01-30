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

### Initialization

On the **Authentication** page of the element, fill in the username and password to connect to the device.

## How to Use

### [1.0.0.x](#tab/version-1-0-0-x)

They are 5 major sections covered in the protocol: **Channels, Input Settings, Descrambling, Output Settings, Encoders and Decoders , and Configuration**.

-- **Channels**: Is identical to the main page of the device where you can monitor and edit the settings applied on each of the channels active on the device. 
-- **Input Settings**: Includes the **DVBS2 Settings** and **SDI Settings** pages which allows to monitor and edit the Input TS and Input Service settings for either standard. 
-- **Descrambling**: Allows the ability to see all the available descramblers and adjust the descrambling mode. 
-- **Output Settings**: Includes the **Output TS**, **Output Service** and **SDI Outputs** pages which allows to monitor and edit the Output TS and Output Service settings.
-- **Encoders and Decoders**: Includes the tables for each of the encoders and decoders which covers features like **Video Pre-Processing**, **Basic Video Settings**, **Basic Audio Settings**, and more which are features on the device.
-- **Configuration**: Showcases the data for the current **Licenses**, **Last 500 Historic Alarms**, and **PCIe Cards** which can be monitored.
