---
uid: Connector_help_Avcom_of_Virginia_EVO-RSA
---

# Avcom of Virginia EVO-RSA

## About

The Avcom of Virginia EVO-RSA is a spectrum analyzer.
This connector is used to retrieve the spectrum traces captured by the analyzer.

## Key Features

- **Real-Time spectrum monitoring**: the captured traces are displayed in real time. The user can configure the common analyzer settings: start and stop frequencies, video and resolution bandwidth,...

## Technical Reference
### Configuration
#### Serial connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

### Prerequisites

- The library **aovsbs2.dll** is needed to establish communication with the spectrum analyzer. The library is included in the connector package and will be installed in the *C:\Skyline DataMiner\ProtocolScripts\DllImport* directory.
