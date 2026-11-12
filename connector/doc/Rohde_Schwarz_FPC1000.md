---
uid: Connector_help_Rohde_Schwarz_FPC1000
---

# Rohde Schwarz FPC1000

## About

The Rohde Schwarz FPC1000 is a spectrum analyzer device.

This connector interfaces with the spectrum analyzer and allows you to monitor the spectrum of any connected signal. The connector communicates with the spectrum analyzer using the VISA (Virtual Instrument Software Architecture) API.

## Key Features

- **Real-time spectrum analysis**: View the live spectrum trace of the connected input signal.

- **Background measurement**: The spectrum trace can be retrieved and analyzed at regular intervals using the built-in spectrum features of DataMiner (Spectrum Monitor and Spectrum Scripts).

## Technical Reference

### Prerequisites

- The VISA library must be installed on the DataMiner Agent. You can download the installer from the [Rohde-Schwarz website](https://www.rohde-schwarz.com/us/driver-pages/remote-control/3-visa-and-tools_231388.html).

- The *RsInstrument.dll* must be present in the *C:\Skyline DataMiner\ProtocolScripts\DllImport* folder of the DataMiner Agent. If you deploy the connector from the Catalog to a cloud-connected DataMiner System, this DLL is automatically stored there. If you install the connector using a .dmprotocol package, the DLL is included and added to the correct location automatically.

### Configuration

On the **General** page, set the **IP address** parameter to the correct IP address of the spectrum analyzer. Once this is done, the spectrum trace will be displayed on the **Spectrum Analyzer** page.
