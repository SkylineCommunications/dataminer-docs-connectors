---
uid: Connector_help_Rohde_Schwarz_FPC1000
---

# Rohde Schwarz FPC1000

## About

The Rohde Schwarz FPC1000 is a spectrum analyzer device.

This connector interfaces with the spectrum analyzer and allows you to monitor the spectrum of any connected signal. The connector communicates with the spectrum analyzer using the VISA (Virtual Instrument Software Architecture) API.

## Key Features

- **Real-time spectrum analysis**: View the live spectrum trace of the connected input signal.

- **Background measurement**: The spectrum trace can be retrieved and analyzed at regular interval using the built-in spectrum features of DataMiner (Spectrum Monitor and Spectrum Scripts).

## Technical Reference

### Prerequisites

This connector requires that the VISA library is installed on the DataMiner Agent. The installer for the library can be downloaded from the [Rohde-Schwarz website](https://www.rohde-schwarz.com/us/driver-pages/remote-control/3-visa-and-tools_231388.html).

In addition, the *RsInstrument.dll* must also be present in the *C:\Skyline DataMiner\ProtocolScripts\DllImport* folder of the DataMiner Agent. If you deploy the connector from the Catalog to a cloud-connected DataMiner System, this DLL will be automatically stored there. If you install the connector via a .dmprotocol package, the DLL will also be included and added in the correct location.

### Configuration
On the **General** page, the parameter **IP address** must be set with the correct address of the spectrum analyzer. Once this is done, the spectrum trace will be displayed when opening the **Spectrum Analyzer** page.